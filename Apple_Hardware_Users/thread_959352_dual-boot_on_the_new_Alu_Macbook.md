---
title: "dual-boot on the new Alu Macbook"
date: 2008-10-26
forum: Apple Hardware Users
---

### Post by months on 2008-10-26
So I have relatively little experience with Ubuntu (I installed 8.04 on an old Dell a week ago) and I am trying unsuccessfully to dual-boot my new aluminum Macbook.  I followed the instructions given for the simple dual-boot installation w/out using rEFit.  I partitioned the hard drive with Bootcamp, and set the /dev/sda3 partition as the mount point and created a swap area (/dev/sda4).  I have tried both 8.10 beta 64 bit and the 8.10 release candidate 64 bit and neither will appear when I hold down alt during startup.  However, both worked using the live CD.  If anyone could tell me what I did wrong or give me some advice that would be great.

---

### Post by kosumi68 on 2008-10-26
The GPT versus MBR synchronization and the blessing of the harddrive are the usual suspects. Did you succesfully bless the drive?

---

### Post by cyberdork33 on 2008-10-26
yep, try this:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

If you don't want rEFIt (don't know why you wouldn't) then you can remove it after you do the fix.

There is also a lot of discussion about the new Macbook here:
[http://ubuntuforums.org/showthread.php?t=947947](http://ubuntuforums.org/showthread.php?t=947947)

---

### Post by months on 2008-10-27
Thanks, I've got Ubuntu working now.  I sacrificed several goats and then used rEFit to synchronize that GPT vs MBP stuff.  Which one did the trick, I can't tell you, but one or the other allows me to run Ubuntu.

---

### Post by cyberdork33 on 2008-10-27
> **months said:**
> Thanks, I've got Ubuntu working now.  I sacrificed several goats and then used rEFit to synchronize that GPT vs MBP stuff.  Which one did the trick, I can't tell you, but one or the other allows me to run Ubuntu.
Thanks for this by the way. I was unsure if this issue still affected Intrepid.

---

