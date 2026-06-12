---
title: "Can't even run from CD"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by dpack on 2006-12-06
I downloaded 6.10. I successfully burned it to CD-R. I was able to boot from the CD and the "CD Verify" process was successful.

When I boot from the CD I'll get past the Ubuntu splash screen and I get to the Ubuntu rectangle shaped box with the light brownish color back drop and will hear the logon wav file, but then it just stops. I never makes it to the next step: the desktop. I tried booting into Safe Graphics mode and it does the same thing. I know my PC is not locked up because I can turn the Num Lock light on and off and I still have mouse cursor movement.

If I can't boot from the CD then there is no way I'll get to the point to where I can install. I've already checked and my graphics card is SUPPOSED to be supported under X. (ATI All-In-Wonder Radeon 8500 128MB AGP - not onboard)

The last Ubuntu system I've been able to successfully run was 5.10. With version 6.06 X Server crashed continually and it was a game of chance just to make it to the desktop including when booting from the CD. Now with 6.10 the problem is consistent. I get no where at all!

Any ideas that don't involve buying new hardware or running Ubuntu in VMWare? Because if that is what it takes I'm sticking with Windows.

---

### Post by ReaderRat on 2006-12-06
If you have onboard video, have you disabled it in the BIOS before using your video card? 

ATI Video - Install the drivers - Edgy - Radeon 
          **[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver)**

---

### Post by wpshooter on 2006-12-06
Do you have another O/S on your computer or is this computer going to be running Ubuntu ONLY ?

---

### Post by dpack on 2006-12-07
I am running an Asus PB4533 mobo. It doesn't have on board video. I have dual SCSI hard drives with WinXP on one drive. I planned to install Ubuntu to the blank second hard drive and dual-boot.

---

### Post by taurus on 2006-12-07
Try the alternate CD...

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by dpack on 2006-12-09
> **taurus said:**
> Try the alternate CD...

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

I burned the Alternate CD and tried the "Install in Text Mode". I made it up to the point where it is on the "Select and Install Software" screen. It hung on that screen at 6% for a while and then finally gave me an error page. The error said the following:

> Installation Setup Failed
An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Select and Install Software.

I hit Continue and jumped past that step and finished the installation. When I boot to Ubuntu I go straight to the command line, which I expected. So, no programs where installed including Gnome.

At this point, I believe I am going to start beta testing Vista. It was worth a shot!

---

