---
title: "Xubuntu will not Boot"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by andrewjuguete on 2008-04-14
I installed Xubuntu a couple of days ago and its been great except now it won't boot.  I absentmindedly pressed the power button to shutdown one day (still used to windows), and now it won't boot.  I don't see a boot screen,  just the lenovo manufacturer screen.   I have no idea what to do.  Any suggestions?

---

### Post by renfrew on 2008-04-14
I'm not a grub expert or anything remotely close, but it sounds like your system can't find the boot image, somethings wrong with your MBR maybe?... 

can you boot the system using the live cd that you presumably installed from??  

You should be able to check the contents of /boot from there for the boot image/files and also check that your grub menu.lst exists.  I'm on a WIN2000 box ( don't ask, its my workplace) as we speak so I can't tell you where menu.lst is as I forget.  You should be able to search for it from within the file manager though.   I'm sure some other GRUB/boot expert will chime in and tell you where to go from here....   although you might have to re-install Xubuntu.

If you can boot from the live cd you should at least be able to backup your data without losing anything.... unless you've got /home on a separate partition, in which case you shouldn't lose anything other than the time to reinstall... :)

---

### Post by canthus13 on 2008-04-14
If you have another computer you can burn images from, try this: [SuperGRUB]("http://supergrub.forjamari.linex.org/").  It has options to repair the MBR. Just boot the CD, choose GNU/Linux, and fix GRUB.

--Me

I just thought about what you said... Does it even boot far enough to say that it can't find the OS, or the drive?  Or does it just hang at the memory count, or drive inventory?  If it hangs without even looking at the drives, you may be looking at an actual disk failure.

---

### Post by ugm6hr on 2008-04-14
This sounds more like a hardware issue.

Most computers will at least tell you that they can't find a bootable drive.

---

