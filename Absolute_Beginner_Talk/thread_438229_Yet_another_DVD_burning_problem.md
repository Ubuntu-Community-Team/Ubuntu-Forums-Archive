---
title: "Yet another DVD burning problem"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by MightyFrog on 2007-05-09
Hi folks,

I installed Feisty Fawn over the weekend, and for the most part things are going very smoothly. I'm unable to burn DVDs, and my situation doesn't quite match any of the other recent threads. 

First off, I can burn CDs just fine, no problem at all. When I insert a blank DVD+R in my drive, Ubuntu recognizes that it's a blank disc and asks me what I'd like to do with it. (I've tried both GnomeBaker and the native file writing for the following.) I select files to burn, the program correctly identifies my burner, and it happily burns the disc. At the end of the process, it says that the burn was successful. I examine the disc and see that it has indeed been burned. I insert it back into the drive . . .

and Linux thinks it's still a blank disc. It can read discs that I used to burn in XP just fine. Could the programs not be closing the discs properly? Any advice appreciated.

---

### Post by Acglaphotis on 2007-05-09
Try with k3b:

```
sudo apt-get install k3b
```

-Acgla

---

### Post by alienexplorers on 2007-05-09
If you have a CD-R disk try burning it to see if you still have the same problem.

---

### Post by MightyFrog on 2007-05-09
Sorry, no dice. This is what I get in the terminal when I put the disc burned with k3b back in the drive:
```

adding udi   /org/freedesktop/Hal/devices/volume_empty_dvd_plus_r
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 553:42:61 (LBA 2491711) (5103024128 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 553:42:61 (LBA 2491711) (5103024128 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ DVD STRUCTURE length det failed
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION with real length 40 failed.
DiskInfo:
Mediatype:       DVD+R
Current Profile: DVD+R
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        35:03:64 (LBA 157789) (323151872 Bytes)
Remaining size:  35:03:64 (LBA 157789) (323151872 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  72
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       3
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE length det failed.
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::Device) /dev/scd0 : 2770 KB/s
removing udi /org/freedesktop/Hal/devices/volume_empty_dvd_plus_r
adding udi   /org/freedesktop/Hal/devices/volume_empty_dvd_plus_r
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 553:42:61 (LBA 2491711) (5103024128 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 553:42:61 (LBA 2491711) (5103024128 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    READ DVD STRUCTURE (ad)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ DVD STRUCTURE length det failed
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ TRACK INFORMATION (52)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: READ TRACK INFORMATION with real length 40 failed.
DiskInfo:
Mediatype:       DVD+R
Current Profile: DVD+R
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        35:03:64 (LBA 157789) (323151872 Bytes)
Remaining size:  35:03:64 (LBA 157789) (323151872 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
(K3bDevice::ScsiCommand) failed: 
                           command:    GET PERFORMANCE (ac)
                           errorcode:  72
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       3
(K3bDevice::Device) /dev/scd0: GET PERFORMANCE length det failed.
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via GET PERFORMANCE: 2
(K3bDevice::Device) /dev/scd0 : 5540 KB/s
(K3bDevice::Device) /dev/scd0 : 2770 KB/s


```

---

