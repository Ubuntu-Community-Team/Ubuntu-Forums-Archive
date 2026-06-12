---
title: "Install Windows AFTER Ubuntu"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-07-03
Hi I have now been running Ubuntu for quite some while, and I may need to dual boot with windows XP.

I have got a spare partition already with about 20gb space that just need to be partitioned ntfs and then I can install windows. This is on the same harddisk as my Ubuntu installation lives.
So I would just use gparted to partition the 20gb disk ntfs, but how do I install windows without messing up GRUB and still by default boot into ubuntu but being able to via grub boot into windows.

---

### Post by pnix on 2007-07-03
I'm not sure can windows install with out destroy grub in mbr. Anyway why you not just install windows and then use liveCD to restore grub again.[ you need to manually add windows menu after grub restore]

---

### Post by r4ik on 2007-07-03
Try,

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Good luck !

---

### Post by kasperbs on 2007-07-16
> **r4ik said:**
> Try,

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Good luck !
Does that work in feisty as well?

---

### Post by Skidpad on 2007-07-16
Try this: [Install Windows (XP) after you've installed Ubuntu]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

---

### Post by Canis familiaris on 2007-07-16
You can use Super GRUB disk in case Windows overwrites the MBR.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by inter-m on 2007-07-16
I dont know if this can help you or not, but try installing Virtualbox. That way you would not need to go through the hassle of dual booting and still have windows working for you...
This is their site [http://www.virtualbox.org/](http://www.virtualbox.org/)
Also you can install it through add/remove...

---

### Post by kasperbs on 2007-07-17
> **inter-m said:**
> I dont know if this can help you or not, but try installing Virtualbox. That way you would not need to go through the hassle of dual booting and still have windows working for you...
This is their site [http://www.virtualbox.org/](http://www.virtualbox.org/)
Also you can install it through add/remove...

Yeah I know VirtualBox and I'm already using it, but as long as [my audio driver in Ubuntu doesn't work]("http://ubuntuforums.org/showthread.php?t=502242") it also [messes up video playback in VirtualBox]("http://ubuntuforums.org/showthread.php?t=491357")

---

