---
title: "Dual Boot Wipe"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by RhynoWoody on 2008-03-14
Hey everybody.  I'm new to Ubuntu (about a month now) and am currently running a dual boot system with Windows XP (which was my OS before).  Thing is, I haven't found the need to use XP since.  So I was getting ready to consider wiping my hard drive of the needless OS, which lead me to a couple of queries.

First off.  I set various peripherals up while i was still on windows (printer, wireless router, etc..).  Each automatically ran when I started dual booting Ubuntu.  I didn't have to set anything up.  Is it too much to hope that since Linux automatically detected all my hardware before, that it will do it if i get rid of windows?

Also, does anyone know of a good website with instructions on the wiping of hard drives?  This would be my first time doing this and I wouldn't want to mess anything up.

Thanks ahead of time.

---

### Post by Duck2006 on 2008-03-14
If you want to wipe your win xp install use gparted live cd to format it to ext3. Boot back into ubuntu and edit your menu.lst to remove your win lines there. In the terminal type.

gksudo gedit /boot/grub/menu.lst

Next add the new partition to your fstab so you can use it.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If you just want to add the new space to your ubuntu partition to make it biger just use gparted to do that with.

---

### Post by Therion on 2008-03-14
If you mean to say when you booted into Ubuntu and it recognized all your hardware without any problem (your printer, router etc.) then you have no reason to believe that it won't without Windows being on your system.  Windows and Ubuntu aren't sharing any kind of information regarding your hardware, Ubuntu was on it's own from the beginning.

To "wipe" your drive of Windows and let Ubuntu have free reign on the drive as your only OS couldn't be simpler.  You boot from a LiveCD and choose:** Guided: Use Entire Drive** at the partitioning segment of the Ubuntu install.  Buh-bye Windows... Hello Ubuntu.  

Make absolutely certain you migrate/backup anything and everything your Windows partition might have, data-wise, that you want to keep.

Or follow Duck's advice, above.  

:)  

Up to you.

---

### Post by canthus13 on 2008-03-14
Just to clarify:  Duck's option will keep your Ubuntu partition intact, while Therion's option will wipe out and reinstall everything, leaving you with a fresh, new copy of Ubuntu.  Personally, I'd go with Duck's option, since it preserves all the settings you've already got, and it's more involved and teaches you a little something about how Linux works.

Canthus13

---

