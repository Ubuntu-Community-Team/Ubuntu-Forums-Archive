---
title: "External HD Issue"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Tenki on 2008-01-04
Ok, so I put Ubuntu on an External HD so that whenever I plug it into my computer I could boot an OS from either my internal HD or my external HD when I open up the BIOS. However, whenever I *do* open up the BIOS I have to choose the internal HD and then choose the OS to bring up Ubuntu and Windows instead of choosing the external HD to boot Ubuntu and choosing the internal to boot Windows. The funny thing is though that all of my files are in tact on the Windows side and everything seems to work fine on the Ubuntu side.

Also, I have to have the HD connected to my computer whenever I open up *any* OS. What can I do to fix my problems?

---

### Post by p_quarles on 2008-01-04
It sounds like you have GRUB (the bootloader) installed on the internal drive. To fix this, you'll have to restore the Windows MBR, and then reinstall GRUB -- but this time, you'll need to specify the external as the install location. 

The bootloaders for both OSes can be restored/installed using the installation disks.

---

### Post by Tenki on 2008-01-04
How would I do that?

---

### Post by p_quarles on 2008-01-04
Reinstalling GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Using the Windows Recovery Console to run "fixmbr":
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by Tenki on 2008-01-05
What does restoring the MBR do?

Also, is restoring the MBR necessary? I can't seem to get to the recovery console. I'm running (or at least trying to) it from my computer since I don't have the installation disc and whenever it starts up this blue screen comes up saying there's a virus or something like that (I can't remember the exact wording of it).

---

### Post by p_quarles on 2008-01-05
> **Tenki said:**
> What does restoring the MBR do?
It restores Windows' ability to boot up directly.

> Also, is restoring the MBR necessary?
Only if you want to be able to boot Windows without plugging in the external drive.

> I can't seem to get to the recovery console. I'm running (or at least trying to) it from my computer since I don't have the installation disc and whenever it starts up this blue screen comes up saying there's a virus or something like that (I can't remember the exact wording of it).
That's more of a Windows question than an Ubuntu question. There are a number of good Windows forums on the internet, but there is also a sub-section of this forum dedicated to Windows questions: [http://ubuntuforums.org/forumdisplay.php?f=170](http://ubuntuforums.org/forumdisplay.php?f=170)

---

