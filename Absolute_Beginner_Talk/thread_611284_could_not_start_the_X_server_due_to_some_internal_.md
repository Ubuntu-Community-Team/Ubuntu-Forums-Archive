---
title: "could not start the X server due to some internal error"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by tuskpc on 2007-11-12
On Sunday I did something to cause my boot up process to stop and give an alert.

  Before I had rebooted I had tried two things; (1)to adjust my screen settings by using System > Admin > Screen and Graphics Preference.  My video card is ATI 7000 Radeon 64mb TVO; I might have got the model info wrong.  (2) I adjusted my fstab by adding "noatime,data=write; got the idea from Linux Format, Nov '07, page 53. 
 
Since then I can only get into the system by rescue mode and Live CD.  I was able to get some info in the various log's.  Is any of this useful info?

---

### Post by Partyboi2 on 2007-11-12
> **tuskpc said:**
> On Sunday I did something to cause my boot up process to stop and give an alert.

  Before I had rebooted I had tried two things; (1)to adjust my screen settings by using System > Admin > Screen and Graphics Preference.  My video card is ATI 7000 Radeon 64mb TVO; I might have got the model info wrong.  (2) I adjusted my fstab by adding "noatime,data=write; got the idea from Linux Format, Nov '07, page 53. 
 
Since then I can only get into the system by rescue mode and Live CD.  I was able to get some info in the various log's.  Is any of this useful info?

Have you tried to remove "noatime,data=write from fstab and see if you are able to boot?

---

### Post by tuskpc on 2007-11-12
Yes.  I tried to with vi, which I'm new too, and nano.  In both cases I got a error telling me it was a read-only file system.  The permission is -rw-r--r-- (ie. value 644).  And just in case someone as:, the type is ext3.  I have 3 partitions on the hard drive: / , /grub , and /home; but I only modified the / options.

The root options were: defaults,errors=remount-ro.
Using gedit, I changed it to: defaults,noatime,data=writeback,errors=remount-ro
saved it, and went on to other things.

I've never used chmod, chown, or chgrp before, so I was hesitant to use it without suggestions from others.

---

### Post by Partyboi2 on 2007-11-12
Try booting into recovery mode and when you get to a terminal type:
```
sudo mount -o remount,rw /
```Then if that works, you should be able to read/write, then you could try making those changes to fstab and see if that fixes your boot problem.

---

### Post by tuskpc on 2007-11-13
Thanks for the help!

It warn me there was no -rw in  fstab or mstab, but when I changed it to -ro it let me edit it.  Now it boots up to graphics.  Again, thank you.

---

### Post by Partyboi2 on 2007-11-13
happy to help :)

---

