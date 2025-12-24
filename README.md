# MIKAZUKI_manual

# nonat clinical_v2 – Technical Specification

## System Requirements

- **Android OS**: 7.0 (API 24) or later, up to 14.0 (API 35)

---

## Communication Specifications

- **Baud rate**: 1,000,000 bps (1 Mbps)
- **Data bits**: 8
- **Stop bits**: 1
- **Parity**: None
- **Flow control**: DTR/RTS control

---

## Data Transmission Format

### Number of Channels
3 channels

### Data Format

Data transmitted from the device is in comma-separated CSV format, terminated by a newline character:

```
FIN_TIP,ARM,FIN_BASE\n
```

- **FIN_TIP**: Channel 1 value (integer, 0–1023)
- **ARM**: Channel 2 value (integer, 0–1023)
- **FIN_BASE**: Channel 3 value (integer, 0–1023)

### Line Termination

- LF (`\n`, 0x0A)

### Transmission Example

```
512,256,768\n
515,258,770\n
510,255,765\n
```

---

## Received Data Processing

- Each line is detected using the newline character (`\n`)
- Each line is split into three values using commas (`,`)
- Each value is parsed as an integer (range: 0–1023)
- Display update rate: up to 20 Hz (50 ms interval)

---

## CSV Recording File Format (Paid Version)

CSV file format during recording:

```
ElapsedTime(ms),FIN_TIP,ARM,FIN_BASE
```

- **ElapsedTime**: Elapsed time since 00:00:00 on the recording start date (milliseconds, integer)
- **FIN_TIP, ARM, FIN_BASE**: Channel values (integers, 0–1023)

### Example

```csv
12345,512,256,768
12395,515,258,770
12445,510,255,765
```

---

## Application Information

- **Version**: 2.01 (Version Code: 8)
- **Minimum Android Version**: 7.0 (API 24)
- **Target Android Version**: 14.0 (API 35)
