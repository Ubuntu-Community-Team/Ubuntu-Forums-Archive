---
title: "BusyBox V 1.1.3  help???"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by lck642 on 2007-11-26
I am trying to install 7.10 and am getting this: BusyBox V 1.1.3 (Debian 1:1.1.3-5 ubuntu7) Buiilt-in shell (ash) enter 'help' for a list of built-in commands
(initramfs)


I currently run windows xp home and OpenSuse10.2

I am trying to install Ubuntu instead of OpenSuse?

How can I do this???

---

### Post by overdrank on 2007-11-26
> **lck642 said:**
> I am trying to install 7.10 and am getting this: BusyBox V 1.1.3 (Debian 1:1.1.3-5 ubuntu7) Buiilt-in shell (ash) enter 'help' for a list of built-in commands
(initramfs)


I currently run windows xp home and OpenSuse10.2

I am trying to install Ubuntu instead of OpenSuse?

How can I do this???

HI and welcome, could you give us some specs on the system? And you can try when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add break=top before the -- then press enter. When you recieve the error again type modprobe piix then hit enter and then type exit then hit enter again this should continue the livecd to boot. 
Hope this helps and good luck!

---

### Post by lck642 on 2007-11-26
the system is an AMD Athlon 2400 1.53GHz with 512MB
I have two HDD one on primary slave and other secondary along with CD-RW combo drive and floppy.

I went into BIOS and disabled the floppy and set boot to CD-RW but for some reason it is not letting me install Ubuntu

I would like to install ubuntu on the secondary and use Grub to load ubuntu or windows

When I installed OpenSuse I already had xp and to be honest I'm not sure if it installed on a separate partition on the primary HDD or on the secondary. I believe it is on the primary b/c it is an 80GB disk and the secondary is 40GB and when I boot into opensuse it shows 75GB of disk space

Any info would help
Thank you

---

### Post by riverstore on 2007-11-27
I get same prolem, after finished install Kubuntu 7.10, Wubi boot to Busybox and I don't know what to do.
My computer:
   - Laptop Acer TravelMate 2428ANWXCi.
   - 1 hard disk, 2 partition: C: NTFS, D: FAT32
   - OS: Windows XP SP2

---

### Post by dingclancy on 2007-12-16
Same Problem --> [http://ubuntuforums.org/showthread.php?p=3965042#post3965042](http://ubuntuforums.org/showthread.php?p=3965042#post3965042)

P.S. The machine ran Ubuntu very well  the first time so it should not be a hardware error

---

