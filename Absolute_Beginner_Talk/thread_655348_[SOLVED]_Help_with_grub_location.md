---
title: "[SOLVED] Help with grub location"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2008-01-01
I have a dual boot with Vista on sda and Ubuntu on sdb but looking at the grub output (below) I'm a bit confused about where grub is installed.
I let grub overwrite the MBR when I installed Ubuntu and things work fine as far as booting both systems.
I'm going to install XP on sdb and know I'll have to reinstall grub, and my question is where do I put it?

fdisk shows:

Disk /dev/sda: 120.0 GB, 120034123776 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14594   117218304    7  HPFS/NTFS


Disk /dev/sdb: 320.0 GB, 320072933376 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       32539   261369486    5  Extended
/dev/sdb2           32540       38670    49246094   83  Linux
/dev/sdb3           38671       38913     1951897+  82  Linux swap / Solaris
/dev/sdb5               1       11473    92156809+   7  HPFS/NTFS
/dev/sdb6           11474       32539   169212613+   7  HPFS/NTFS



But then I get the following output from grub:

grub> find /boot/grub/stage1
 (hd1,1)

From this, it shows grub on sdb doesn't it?
When I reinstall grub to the MBR would I put it on hd1 or hd0 ?

Sorry for the confused post; Any help would be appreciated.

---

### Post by Moop on 2008-01-01
I think it's best to put grub on a non-windows hard drive if you have one but that's just my preference. As long as grub is on the hard drive you're booting from everything should workout fine.

---

### Post by Milt888 on 2008-01-01
> **Moop said:**
> I think it's best to put grub on a non-windows hard drive if you have one but that's just my preference. As long as grub is on the hard drive you're booting from everything should workout fine.

Agreed; but if grub is on the MBR, or sda (wouldn't that be) hd0 ?
What's confusing me is it's showing up on hd1,1.
I know I'm going to have to reinstall grub, I just wondered "where do I put it".
Thanks--Milt

---

### Post by Moop on 2008-01-01
If I have 1 windows hdd then the mbr is there. If I add a hard drive and install Ubuntu then it will write the mbr to the new hdd. How that affects the windows hdd, I don't really know.

I suppose I'm as confused as you. :) But it seems normal to me that grub is on hd1.1 in your situation.

---

### Post by Milt888 on 2008-01-01
> **Moop said:**
> If I have 1 windows hdd then the mbr is there. If I add a hard drive and install Ubuntu then it will write the mbr to the new hdd. How that affects the windows hdd, I don't really know.

I suppose I'm as confused as you. :) But it seems normal to me that grub is on hd1.1 in your situation.

I agree with you Moop, It's on the Ubuntu drive evidently (sdb) but the original Vista MBR is on sda.
I don't know, but it works.
I'm just going to put it back on hd1. Guess I can always change it.
Thanks--Milt

---

### Post by logos34 on 2008-01-01
> **Milt888 said:**
> Agreed; but if grub is on the MBR, or sda (wouldn't that be) hd0 ?
What's confusing me is it's showing up on hd1,1.
I know I'm going to have to reinstall grub, I just wondered "where do I put it".
Thanks--Milt

'Grub-install' writes the stage1 file in /boot/grub folder to the MBR of the hard drive...what 'find' is showing is the location of the original file in /boot/grub on the root partition, sdb2 (aka hd1,1).  

Grub is on the mbr of sda.  That's what you're booting.  But to install XP on sdb you'll have to change the Bios hard disk boot priority (temporarily) so that sdb is first.  XP bootloader will install to the mbr of sdb.  After installation is complete, change the boot order back and boot to grub.  Go into ubuntu and add a XP stanza/entry to menu.lst [with map commands to chainload windows on a non-first hard disk]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").  Let's say you put XP on sdb5:

> title           Windows XP
root            **(hd1,4)**
savedefault
makeactive
[B]map            (hd0) (hd1)
map            (hd1) (hd0)[/B]
chainloader     +1

---

### Post by Milt888 on 2008-01-01
> **logos34 said:**
> 'Grub-install' writes the stage1 file in /boot/grub folder to the MBR of the hard drive...what 'find' is showing is the location of the original file in /boot/grub on the root partition, sdb2 (aka hd1,1).  

Grub is on the mbr of sda.  That's what you're booting.  But to install XP on sdb you'll have to change the Bios hard disk boot priority (temporarily) so that sdb is first.  XP bootloader will install to the mbr of sdb.  After installation is complete, change the boot order back and boot to grub.  Go into ubuntu and add a XP stanza/entry to menu.lst [with map commands to chainload windows on a non-first hard disk]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").  Let's say you put XP on sdb5:

Ahh.. That explains it so even I can understand.
I'll follow those instructions.
Thanks much logos.

---

