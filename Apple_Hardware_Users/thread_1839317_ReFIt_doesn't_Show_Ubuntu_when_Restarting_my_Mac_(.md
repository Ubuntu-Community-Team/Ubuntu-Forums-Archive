---
title: "ReFIt doesn't Show Ubuntu when Restarting my Mac (I'm Trying to Install from via USB)"
date: 2011-09-05
forum: Apple Hardware Users
---

### Post by swalker133 on 2011-09-05
Hi, I am trying to install Ubuntu on my Mac running Lion.

I did everything shown here:
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick")
I'm pretty sure that I did everything there right because when i insert the USB jump drive into my computer, it's entitled, "Ubuntu 11.04 amg" 

But, when i reboot my macbook with the USB disk plugged in, reFIt doesn't show Ubuntu as an option, I only get mac, and another option that says, "Boot Legacy OS from HD"

When i select "Boot Legacy OS from HD," it shows a black screen that says, "Non-system Disk. Press any key to continue" and it wont let me press any key to continue; pressing any key does nothing...

---

### Post by sviola on 2011-09-05
Which system are you using? I know there are many Macs that don't allow you to boot from USB. For example, I have a MacBook5,1 and it doesn't work, even when I follow the directions that you did.

---

### Post by swalker133 on 2011-09-05
> **sviola said:**
> Which system are you using? I know there are many Macs that don't allow you to boot from USB. For example, I have a MacBook5,1 and it doesn't work, even when I follow the directions that you did.

I have a MacBook, not sure which one, but when i clock "About this Mac," it says:

"MacBook
13-inch, Late 2009
Processor  2.26 GHz Intel Core 2 Duo
Memory  2 GB 1067 MHz DDR3
Graphics  NVIDIA GeForce 9400M 256 MB
Software  Mac OS X Lion 10.7 (11A511)"

I think it's the last model of the macbook...

---

### Post by swalker133 on 2011-09-05
Here's a link to the macbook i have:
[http://support.apple.com/kb/SP579?viewlocale=en_US]("http://support.apple.com/kb/SP579?viewlocale=en_US")

---

### Post by DoubleClicker on 2011-09-05
Macs can boot off of usb, but they can only boot from drives with a GUID partition table.  first format the usb drive disk using Disk Utiility, as a normal mac drive.  Then follow the instructions, but in the replace where it says diskN use diskNs2 instead
N with the disk number and s2 is the partition number)

for example
```
 $> diskutil list

/dev/disk0
   /dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *1.0 TB     disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Mac OS X                 89.1 GB   disk0s2
   3:                  Apple_HFS Data                    880.7 GB   disk0s3
   4:       Microsoft Basic Data Ubuntu                   15.1 GB   disk0s4
   5:       Microsoft Basic Data Testing                  13.9 GB   disk0s5
   6:                 Linux Swap                          1.2  GB    disk0s6

/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                          *2.0 GB   disk2
   1:                          EFI                       209.7 MB   disk2s1
   2:        Microsoft Basic  LiveUSB                      1.9 GB   disk2s2

```
You would use:
```
$> sudo dd if=/path/to/downloaded.img of=/dev/disk1s2 bs=1m
```

---

