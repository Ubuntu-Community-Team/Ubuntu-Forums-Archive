---
title: "[SOLVED] Error 15 on boot"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by enofman on 2008-03-11
I have install Ubuntu 7.10 Gutsy Gibbon 64 bit and everything was running just fine for about 2 1/2 months until today..  I had installed XAMPP and XAMPP started doing really strange things, so I thought a removal and reinstall would be the easiest way to remove the problems.  However, when i ran the command rm -rf /opt/lampp which is where XAMPP is installed the entire computer froze and rebooted.  Now when I boot I get a msg about grub booting and please wait followed by an error 15 right under the please waiting.  I do not have a dual boot system.  I would not have a problem just moving the information to another drive because I can boot from the live CD.  However I can not find any of my folders on the partition which holds all the information.  I can get to the desktop information, however I had a folder for my downloads and documents which I created and I need those files.  I also do not know if I need to move anything back from the 7.9 gb which is on the hard drive now.  ANY help will be much appreciated.

Thanks
Gary

---

### Post by justleen on 2008-03-11
if you have an usb stick and a live cd lying around: get SuperGrub, make a bootable USB drive (and keep that for time to end).

Boot of the USB, and follow the instructions..

Supergrub will be able to restore grub easily. It might seem a lot of work, but i think its worht it.
[URL="http://ubuntuforums.org/showthread.php?t=224351"]

Offcourse, a quicker way is just reinstalling grub from the live cd [/URL]

---

