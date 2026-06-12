---
title: "A quasi technical question"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by ayesha kalra on 2008-01-02
Hi all

My question is that my desktop ( A dell with dual-core AMD processor, 1Gb RAM) is making a lot of noise, The noise is not that of the fan, is it an irritating kit-kit-ki-kit-kit---- noise whenever I click something or a new page is opening etc. Also the noise is prominent while booting up and shutting off. Otherwise, it is intermittent.

One of my friend said that it is due to accumulation of dust on the motherboard and/or in the hard drive. It seems that this noise is also slowing my computer down. Any suggestion will be helpful here, sorry for being imprecise.

Thanks
Ayesha

---

### Post by ~LoKe on 2008-01-02
If it's not the fans then it's your hard drive.  Sounds to me like it's dying.

---

### Post by jken146 on 2008-01-02
Loose fans and old hard drives do this quite often.

---

### Post by crjackson on 2008-01-02
That my friend is likly the "Click of Death" for your HD.  I hope it's still covered by Dell.

---

### Post by ~LoKe on 2008-01-02
> **jken146 said:**
> Loose fans and old hard drives do this quite often.

Hm...Old IDE hard drives might make this noise, you're right.  But if his system is actually running slower, I'd blame it on a failing drive.

---

### Post by marx2k on 2008-01-02
Sounds like the hard drive telling you you need to replace it. Paste the output of the following command:
```

sudo smartctl -a /dev/sda

```

---

### Post by ayesha kalra on 2008-01-02
```

sudo: smartctl: command not found

```

---

### Post by ~LoKe on 2008-01-02
> **ayesha kalra said:**
> ```

sudo: smartctl: command not found

```

```
sudo apt-get install smartmontools
```
That should work.

---

### Post by ayesha kalra on 2008-01-02
```

smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.9 family
Device Model:     ST3160812AS
Serial Number:    9LS5JEBL
Firmware Version: 3.ADJ
User Capacity:    160,000,000,000 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jan  2 23:15:40 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Total time to complete Offline
data collection:                 (   0) seconds.
Offline data collection
capabilities:                    (0x00)         Offline data collection not supported.
SMART capabilities:            (0x0000) Automatic saving of SMART data                                  is not implemented.
Error logging capability:        (0x00) Error logging supported.
                                        General Purpose Logging supported.

SMART Attributes Data Structure revision number: 3162
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
255 Unknown_Attribute       0x373f   200   016   063    Pre-fail  Always   In_the_past 69269232549888
 32 Unknown_Attribute       0x2020   032   032   032    Old_age   Offline  FAILING_NOW 76223677549600
 76 Unknown_Attribute       0x0042   000   000   066    Old_age   Always   FAILING_NOW 74986605773888
 32 Unknown_Attribute       0x204a   032   084   074    Old_age   Always   FAILING_NOW 54108806656339
 65 Unknown_Attribute       0x2032   083   032   050    Old_age   Always   In_the_past 35322350018592
 32 Unknown_Attribute       0x2020   032   032   032    Old_age   Offline  FAILING_NOW 35322350018592
 32 Unknown_Attribute       0x2020   032   032   032    Old_age   Offline  FAILING_NOW 550026354720
 16 Unknown_Attribute       0x3f00   000   016   000    Old_age   Offline  FAILING_NOW 280380028550140
255 Unknown_Attribute       0x000f   000   007   015    Pre-fail  Always   FAILING_NOW 131943408599808
240 Head_Flying_Hours       0x7800   000   000   000    Old_age   Offline  FAILING_NOW 0
 64 Unknown_Attribute       0xfe00   000   000   000    Old_age   Offline  FAILING_NOW 38994028292864
104 Unknown_Attribute       0x0134   052   035   052    Old_age   Offline  FAILING_NOW 4226880
254 Unknown_Attribute       0xfefe   255   000   254    Old_age   Always   In_the_past 13631488
 32 Unknown_Attribute       0x0220   000   182   032    Old_age   Offline  FAILING_NOW 6599385022978
 10 Spin_Retry_Count        0x003c   000   198   060    Old_age   Offline  FAILING_NOW 22024592359431
  2 Throughput_Performance  0x0002   000   004   002    Old_age   Always   FAILING_NOW 4

SMART Error Log Version: 90
Invalid Error Log index = 0x0c (T13/1321D rev 1c Section 8.41.6.8.2.2 gives valid range from 1 to 5)

SMART Self-test log structure revision number 3162
Warning: ATA Specification requires self-test log structure revision number = 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging


```

I can see the failing now :(

---

### Post by marx2k on 2008-01-02
Yep. I would call that the 'worst case scenario' - On the bright side, you have a chance to back up your data

[EDIT] - Looking at that output, it also says you did not enable SMART diagnostics. Are you able to do so in your BIOS? You should go into your BIOS, enable SMART Hard Drive diagnostic feature (most up to date BIOSes have that ability) and re-run the command and see if it changes.

---

