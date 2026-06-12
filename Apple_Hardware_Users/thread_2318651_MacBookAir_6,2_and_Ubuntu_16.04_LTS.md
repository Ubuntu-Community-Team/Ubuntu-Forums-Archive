---
title: "MacBookAir 6,2 and Ubuntu 16.04 LTS"
date: 2016-03-28
forum: Apple Hardware Users
---

### Post by gwillem on 2016-03-28
16.04 installation on my MBA6,2 went quite flawless, I could skip half of the old [14.04 instructions]("https://help.ubuntu.com/community/MacBookAir6-2/Trusty"). 

There are some issues with power management though. After resuming from suspend, the SATA link is wonky and repeatedly (5 sec interval) gives:

```
Mar 28 13:13:29 travira kernel: [  891.865354] ata1.00: exception Emask 0x10 SAct 0x1000 SErr 0x4040000 action 0xe frozen
Mar 28 13:13:29 travira kernel: [  891.865357] ata1.00: irq_stat 0x80000040, connection status changed
Mar 28 13:13:29 travira kernel: [  891.865359] ata1: SError: { CommWake DevExch }
Mar 28 13:13:29 travira kernel: [  891.865361] ata1.00: failed command: WRITE FPDMA QUEUED
Mar 28 13:13:29 travira kernel: [  891.865365] ata1.00: cmd 61/58:60:80:02:d5/00:00:06:00:00/40 tag 12 ncq 45056 out
Mar 28 13:13:29 travira kernel: [  891.865365]          res 50/00:00:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
Mar 28 13:13:29 travira kernel: [  891.865366] ata1.00: status: { DRDY }
Mar 28 13:13:29 travira kernel: [  891.865369] ata1: hard resetting link
Mar 28 13:13:30 travira kernel: [  892.589359] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Mar 28 13:13:30 travira kernel: [  892.589783] ata1.00: unexpected _GTF length (8)
Mar 28 13:13:30 travira kernel: [  892.590268] ata1.00: unexpected _GTF length (8)
Mar 28 13:13:30 travira kernel: [  892.590328] ata1.00: configured for UDMA/33
Mar 28 13:13:30 travira kernel: [  892.590375] ata1: EH complete
```

And sometimes (1 out of 5) a resume fails and I have to hard-reset the MBA. Haven't been able to establish a common denominator yet.

Anyone got a pointer?

Here is my smartctl -a output:

```
SMART Attributes Data Structure revision number: 40
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   000    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x000f   100   100   000    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       827
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2083
169 Unknown_Attribute       0x0022   100   100   010    Old_age   Always       -       738908440288
173 Wear_Leveling_Count     0x0022   196   196   100    Old_age   Always       -       8598847516
174 Host_Reads_MiB          0x0030   100   100   000    Old_age   Offline      -       1793040
175 Host_Writes_MiB         0x0030   100   100   000    Old_age   Offline      -       1552935
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       142
194 Temperature_Celsius     0x0022   043   043   000    Old_age   Always       -       57 (Min/Max 24/81)
197 Current_Pending_Sector  0x0032   000   000   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
244 Unknown_Attribute       0x0002   000   000   000    Old_age   Always       -       0
```

---

### Post by wmoore on 2016-04-08
This is great news. I currently run 14.04 and an pretty happy with it. I actually never suspend due to the black screen on resume issue so that wouldn't bother me. But the fact that everything else works just makes me want to hit upgrade tomorrow!

Did you install 16.04 from scratch or upgrade?

---

### Post by johnkenyon on 2016-07-18
Sounds like this might be related:
[https://wiki.archlinux.org/index.php/MacBook#Marvell_ATA_suspend_bugs](https://wiki.archlinux.org/index.php/MacBook#Marvell_ATA_suspend_bugs)

---

### Post by johnkenyon on 2016-07-18
Sounds like this might be related:
[https://wiki.archlinux.org/index.php/MacBook#Marvell_ATA_suspend_bugs](https://wiki.archlinux.org/index.php/MacBook#Marvell_ATA_suspend_bugs)

---

### Post by awjrichards on 2016-08-20
Awesome. I took this post as inspiration to install 16.04 on my MacBook Air 6,2 as well. If you haven't already, try patjak's [mba6x_bl backlight driver ]("https://github.com/patjak/mba6x_bl")- after installing that and switching to the 4.4.0-34-generic kernel, my suspend issues seem to have gone away (though I admittedly haven't thoroughly tested it yet).

---

