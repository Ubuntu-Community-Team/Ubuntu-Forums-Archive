---
title: "Windows/Linux: Dual boot - dual disk"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by dawhoo on 2006-04-02
I had installed Ubuntu and the grub boot manager, but was unable to boot to windows.  Here's what I did to fix my installation, maybe it will help someone else. THis assumes you have an extra HD around somewhere.  I have about 10 of them. 

I had Win2K on one HD (sda1) with a blank 20GB partition for linux. Installed fine and installed grub to the sda1 MBR.  After install, it would boot to linux, but not windows :(  I put in the windows disk, booted and opted for maunual repair mode. I typed "FIX MBR".  Now, I was able to boot to windows, but not linux. 

No biggy. I hadn't tweaked Ubuntu and it installs quickly anyway.  I figured I would just reinstall it to its own disk and not make it share with windows. 

I had another HD around, so I put in the new HD (hda1) and installed linux on that disk.  When it asked to instal grub, I had it install it on the hda1 MBR rather than the sda1, but it still recognized Win2k as being present - excellent!

I reboot the computer and it immediately goes to windows.  Why?  Because I had sda1 set in BIOS as the primary boot drive. 

So, I went into BIOS and changed boot disk priority to boot to hda1, rather than sda1. Now, grub comes up and shows my windows install in the list and I can boot to windows or ubuntu without problem :D

The good part of this is my sda1 MBR is untouched, so if I needed to, I could remove the other linux HD (hda1), my systems boots to windows without any problem. 

I have no idea if this is a good thing or a bad thing I have done, but I know it works and my windows MBR is untouched and completely functional on its own if needed, which I feel is a good thing.

---

### Post by Sutekh on 2006-04-02
That sound just fine.  I installed my dual boot in exactly the same way.  

In addition (if you are interested) I have several Linux installations on the second disc with Ubuntu.  Ubuntu's GRUB was allowed to install to the MBR of the second disc, but for every subsequent OS I install, I direct their bootloaders to be installed in *their* specific partition.  This way Ubuntu's GRUB still resides in the MBR.  It means that I have to update GRUB with the new information, but keeps things neater IMO.

---

