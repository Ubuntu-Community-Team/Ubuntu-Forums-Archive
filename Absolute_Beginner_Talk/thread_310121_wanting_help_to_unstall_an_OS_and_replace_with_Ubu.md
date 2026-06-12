---
title: "wanting help to unstall an OS and replace with Ubuntu"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Revmann on 2006-11-30
I am a Linux noob. I messed around a little bit with Breezy some months ago. I gave up Linux for a while, but recently wanted to get it going again. For kicks, I installed the Xandros trial, but even if it were free, I didn't care for it. I want to get rid of Xandros and go with Ubuntu or Kubuntu. 

I don't want to get rid of the Windows partition yet and don't want to mess up any data there. I do want the Xandros gone along with that bootloader. Is it possible to remove those and put in its place a version of Ubuntu with the grub bootloader without disturbing the windows partition?

---

### Post by xabbott on 2006-11-30
Yes. If Xandros created two partitions (/ and swap) then you would just reformat those (or just /). Then install Grub. Should be fine.

---

### Post by rbprogrammer on 2006-11-30
what i would do is use partition magic in windows to completely erase every partition except for the windows partition and then restart the computer and put the ubuntu/kubuntu CD in the drive and boot up from the cd.  the installer on the cd will allow you to install ubuntu and then install a new boot loader.  but remember to erase the partitions when you know you do not need any data from them.

---

