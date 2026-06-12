---
title: "Problem with USB boot iso images for v 10.4 on a MBP"
date: 2014-09-10
forum: Apple Hardware Users
---

### Post by dcnicholls on 2014-09-10
Background: I want to install Ubuntu as a dual boot option on my 2009 Macbook Pro (5.3).  The Ubuntu site says the most recent version of Ubuntu that works on that model is 10.04  The DVD drive is defective so won't read a disk image.  So I want to boot/install from a USB image.

Problem: I cannot get the v10.04 image to burn a bootable UDB.  I _can_ get the v 14.04 image to work as a bootable image.

Observation: If I open the various iso files I have downloaded using the Mac OS X DiskImageMounter, it shows the contents of the version 10 Ubuntu iso, but the version 14 says "no mountable file systems".  The one I can't read using DiskImageMounter is the only one that works as a bootable iso/img.  Can anyone tell me what's going on?

I have read extensively the various instructions to convert the iso to an img file, and how to write this to the USB stick.  It _does work_ with version 14, but not with version 10. Exactly the same results on the old MBP and a newer Mavericks MBP.

Help appreciated.

DN

Supplementary: I notice the iso images that don't work as bootable files have .inf and .exe files included.  Might this indicate the iso was intended for a Windows environment rather than a Mac?

---

### Post by oldfred on 2014-09-10
Desktop version of 10.04 is obsolete.
       Please see this sticky thread in the Installation subforum.
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

This says 12.04, but I do not know Mac and versions. Uusally the newest works better as it has more updates.
      
 [URL="https://help.ubuntu.com/community/MacBookPro"]https://help.ubuntu.com/community/MacBookPro
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[/URL]

---

### Post by dcnicholls on 2014-09-10
Thanks for that.  I'll see what v12 does and report back.

Thanks, that install worked, however, while I can run the "Try Ubuntu..." process, I can't install it.  See my next post, [http://ubuntuforums.org/showthread.php?t=2243774](http://ubuntuforums.org/showthread.php?t=2243774)

---

