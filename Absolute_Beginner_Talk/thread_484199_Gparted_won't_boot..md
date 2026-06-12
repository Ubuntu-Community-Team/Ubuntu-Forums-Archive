---
title: "Gparted won't boot."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-06-25
I downloaded and burned two versions of gparted and neither of them loaded at boot up. It goes right into grub.

---

### Post by wormser on 2007-06-25
Have you changed your boot order in the BIOS to boot the CD first?

---

### Post by loserboy on 2007-06-25
are you burning it as an image and are you sure its the bootable version

---

### Post by henthorn on 2007-06-25
I thought I was burning an iso from the official site. I have doen the same with other versions and had no problems except with the most recent which just flat froze in the process.

---

### Post by ugm6hr on 2007-06-25
> **henthorn said:**
> I thought I was burning an iso from the official site. I have doen the same with other versions and had no problems except with the most recent which just flat froze in the process.

This is the official .iso:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

If you have your BIOS set to boot from CD first, and you have correctly burnt the iso as a CD image (rather than data file), then the GParted GRUB will boot.

The only reasons not to get as far as the GParted GRUB selection are:
error in .iso download / writing;
incorrect BIOS boot order;
CD drive not working.

I have used this latest version - and it works fine on PCs.

---

### Post by henthorn on 2007-06-25
Thanks, It is burned as an iso which I guess means that it is an image.  To further compound the problem, I tried the latest version and it boots up grub just fine but freezes the computer half way thrugh the process. I have downloaded it twice and it still does that.  Next I tried the June 2006 2.5.2 version and it booted into grub just fine, but it doesn't have the ntfs features I need.  Then I tried 3.4.1, 3.4.2, and 3.4.4 and none of them would bring up grub.  It just went right to choice.  I'm befuddled.

---

### Post by loserboy on 2007-06-25
do you have access to another computer that you can test that disk on just to confirm?

---

### Post by henthorn on 2007-06-25
No, I've just got the one.  However it wasn't just one disk, but three different disks with three different versions.

---

### Post by ugm6hr on 2007-06-26
I'm a bit confused - does the GParted LiveCD bring up it's own GRUB, or your computers internal hard drive GRUB?

If you get to the GParted GRUB - select the second option rather than first - that should allow it to edit itself for your hardware.  If that doen't work either, try some of the other options (I've not tried any others).

If you don't get to the GParted GRUB - then if it isn't any of the problems I listed previously, I have no idea.

---

### Post by henthorn on 2007-06-26
I guess I am out of luck with Ubuntu since no one seems to have clue to this strange problem. I have since downloaded the newest edition of gparted twice and version 3.4-6 twice, one from a different mirror site and each one of them boots into grub and then quits before finishing with the "unsupported mode" message on the monitor diagnostic box.

I guess my only option is to re-format the hard drive and try again. I'm not sure it is worth the effort.
Thanks for your advice.

---

### Post by ugm6hr on 2007-06-26
Presumably you tried all of the GParted GRUB boot options?  From memory - there were at least 5 or 6 different options.  As mentioned - the 2nd boot option worked for me.

I'm assuming that the problem with Ubuntu is that you only have 1 hard drive with Windows on already in a single NTFS partition.

If so - Partition Magic will shrink the Windows partition for you if you have it (or Vista has a built-in function).

---

