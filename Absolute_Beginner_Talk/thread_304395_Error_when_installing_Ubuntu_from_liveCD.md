---
title: "Error when installing Ubuntu from liveCD"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Faluzure on 2006-11-21
Hey. Just like to say first that I am impressed with the liveCD.

I'm trying to install the OS from it, and I get as far as the partitioning step. When I try an format the hard drive, I get an error message at 5%. 

"Failed to create a file system, The ext3 file system creation in partition #1 of SCSI6(0,0,0)(sdg) failed.

The message comes up at "Creating ext4 file system for / in partition #1 of SCSI6(0,0,...", in the install progress window.

I've tried this with two separate hard drives(80gb,120gb), both giving me the error at 5%. I've got the hard drives hooked up though a USB interface. I'd rather not take apart my machine again to see if its a problem with the USB interface. Any help is greatly appreciated. 

Thanks
-Joe

---

### Post by seijuro on 2006-11-21
Might try checking the install disc for defects least if it were me I'd check that before opening up my machine. Maybe burn a fresh iso.

---

### Post by Faluzure on 2006-11-21
I scanned the CD with the included utility when the CD boots. The bar fills up and then nothing happens. If I hit enter, it reboots. Im assuming that means the CD is corrupted.

---

### Post by ReaderRat on 2006-11-21
**[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)**
Check the MD5sums on the .iso you downloaded first...should be found where you d/l the .iso . Use a good (not a no-name) CD-R. Burn at a low speed (4X, 8X if your CD-RW won't go that low). And use the boot option to check the files on the disc (as you have done) when you boot it. Good Luck...

---

