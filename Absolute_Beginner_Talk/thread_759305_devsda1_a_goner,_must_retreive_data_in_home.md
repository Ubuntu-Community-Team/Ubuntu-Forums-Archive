---
title: "/dev/sda1 a goner, must retreive data in /home"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-04-18
I jammed the /dev/sda1 and have to copy or preserve somehow my /home "folder".

I have a 40 gig drive in an external usb case. 

sudo lsusb
Bus 004 Device 004: ID 3538:0054 Power Quotient International Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 07e5:5c01 QPS, Inc. Que! CDRW
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 04f9:01ab Brother Industries, Ltd 
Bus 001 Device 006: ID 13fe:1a00  
Bus 001 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 005: ID 03eb:3301 Atmel Corp. at43301 4-port Hub
Bus 001 Device 001: ID 0000:0000  

but I can't access the drive in a LiveCD session. At least it doesn't show up in Places/Computer.

What needs doing?

---

### Post by joshrobinson on 2008-04-18
what filesystem is the external usb drive?
can you post the output of

```
fdisk -l
```

---

### Post by Mark_in_Hollywood on 2008-04-18
sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  83  Linux

Disk /dev/sdc: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x417fc429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         984      251888    e  W95 FAT16 (LBA)

by the by: the usb external is listed as cdrw, but I have a 40 gig drive in it. I hope that's not making this moot!

My guess is that the 40 gig has (bad taste in my mouth) m$.

---

### Post by Mark_in_Hollywood on 2008-04-25
I have my entire /dev/sda1 "recovered". By allowing GParted to perform it's "test" function, it has found the multiply-claimed blocks in inode: xxxxx and the 320 gig drive is all good.

I had four or five different posts regarding the problem over the course of several weeks. 

Thread Closed -- Ubuntu Success!!!

---

