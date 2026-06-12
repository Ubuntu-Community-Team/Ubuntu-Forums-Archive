---
title: "I have to re-install Windows, oh dear.."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-27
Well yesterday I had a nasty virus on Windows, I decided instead of looking into the problem, hell I'll just leave that mess behind, well now I actually need Windows, as I use Adobe Photoshop alot and I've been trying to scratch the surface in Visual Basics. Befor I made a small 15 gig partition for Windows and some applications I remember reading that if you were gonna install Windows on your LInux system, that you would have to re-install Windows of LInux, and then re-install Linux as the 2nd OS :confused: So is it true that I Have to erase Linux if I want to use Windows for minor things?

---

### Post by BarfBag on 2007-04-27
That's partially true.  Each time you install/reinstall Windows, it clears your MBR (Master Boot Record).  The MBR is where Grub (the boot loader) is stored.  As long as you don't touch your Linux partition in the partitioning options, your installation should still be there; but you won't be able to boot into it.  I'm sure there's a way to reinstall Grub, but it's probably easier just to do a reinstall.

---

### Post by Sef on 2007-04-27
Read [Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by lamalex on 2007-04-27
you could also just use vmware. and monodevelop for VB.

---

### Post by orb9220 on 2007-04-27
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by Lucifiel on 2007-04-27
If I were you, go take some precauations and use Partimage to backup your Ubuntu installation. This is in case your partition can't be recovered. 

Look here on how to backup with Partimage
[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

---

