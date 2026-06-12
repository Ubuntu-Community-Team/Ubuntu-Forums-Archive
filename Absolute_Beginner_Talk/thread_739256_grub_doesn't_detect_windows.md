---
title: "grub doesn't detect windows"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by nagao88 on 2008-03-29
hi, i've just installed ubuntu on a partition of my computer (which is windows xp) and been using it happily for a few days. then i decided i'd quite like to run a program which i have for windows xp, so i tried to boot into it. but grub somehow doesn't detect it! 

when i run sudo fdisk -l the output is:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49ce3bb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

how do i boot into windows? thanks!

---

### Post by TeoBigusGeekus on 2008-03-29
Open a terminal and type
```
sudo gedit /boot/grub/menu.lst
```
that's LST.
Post the contents of the file.

---

### Post by Duck2006 on 2008-03-29
> Device Boot Start End Blocks Id System
/dev/sdb1 1 14593 117218241 7 HPFS/NTFS

It windows is on your slave, then you have to map it to boot.
Edit your menu.lst as "TeoBigusGeekus" posted and add these lines.

> #title          Windows NT/2000/XP
#root           (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
#savedefault
#chainloader    +1

---

### Post by nagao88 on 2008-03-29
umm... this is what my menu.lst looks like...

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=413d63db-6a13-4427-9788-09be60eee48f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=413d63db-6a13-4427-9788-09be60eee48f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

do i add another entry or something?

---

### Post by Duck2006 on 2008-03-29
In the terminal, Applications>>Accessories>>Terminal to open the terminal, Then type to edit the menu.lst

gksudo gedit /boot/grub.menu.lst

add these lines

title Windows NT/2000/XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader +1

save and then reboot it and you should have windoze in your menu.

---

### Post by nagao88 on 2008-03-29
well, now i have windows on my grub menu, but when i select it, it says:
a disk read error occurred. press ctrl+alt+del to restart.
when i restart, it says error: selected disk does not exist. 

what's going on?

---

### Post by Duck2006 on 2008-03-29
> selected disk does not exist.

When you just had windoze on your system did you have it installed on the first drive, and used the second drive for data?

---

### Post by nagao88 on 2008-03-29
nope, i just had the one drive, and i partitioned it when i installed ubuntu.

---

### Post by Duck2006 on 2008-03-29
The other way around it is to use the super grub dick to do it with.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

And some reading on grub.

rs.bigpond.net.au/hermanzone/p15.htm

---

### Post by mikewhatever on 2008-03-29
> **nagao88 said:**
> nope, i just had the one drive, and i partitioned it when i installed ubuntu.

Are you sure? Fdisk command shows there are two hdds, /dev/sda and /dev/sdb. Is that incorrect?

---

### Post by nagao88 on 2008-03-29
i'm pretty sure i've only got one hard drive... it's a laptop, and i just got the new hard drive 2 days ago. i was wondering what that sda and sdb thing meant.

---

### Post by Duck2006 on 2008-03-29
Does your system have a recovery partition?

---

### Post by nagao88 on 2008-03-29
yep...

---

### Post by Duck2006 on 2008-03-29
I would say you have installed ubuntu over your win xp install and whats showing up when you do a fdisk -l just show the recover partition. So yes it would come back with a

> error: selected disk does not exist.

If you want xp you are going have to make room and them reinstall xp again.

If that what you want to do here is a how to for that.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by nagao88 on 2008-03-29
hmm... the problem is that i don't have a windows cd, just a recovery cd which will wipe everything.

---

### Post by louieb on 2008-03-29
> **Duck2006 said:**
> In the terminal..
I agree with Duck2006 but try a small change in the order of the lines in the entry and change root to rootnoverify.  I have XP on my 2nd drive and I know this will work.
```

title Windows NT/2000/XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
savedefault
chainloader +1

```

According to the fdisk output you have 2 hard drives. Ubuntu on the 1st and XP on the 2nd or you have an external drive plugged. 
Do you have and external drive plugged in?

Also your fdisk output is a little weird  in that the 1st line is missing (disk  size) was that a cut and paste where you didn't get the 1st line?

At this point Duck2006 suggestion of using  the [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") may be the easiest way to go.

---

### Post by nagao88 on 2008-03-29
oh that's true,,, i do have an external drive. so if the fdisk is detecting that, does that mean it can't detect my windows installation?

---

### Post by Duck2006 on 2008-03-29
> **nagao88 said:**
> oh that's true,,, i do have an external drive. so if the fdisk is detecting that, does that mean it can't detect my windows installation?

That show that you use the complete disk for you ubuntu install.

---

### Post by nagao88 on 2008-03-29
but the ubuntu install only shows 40gb... how do i access the other 80gb which i seem to have partitioned away?

---

### Post by Duck2006 on 2008-03-29
Post the full out put of

fdisk -l

from the terminal

---

### Post by nagao88 on 2008-03-29
after i removed my external hard drive, it looks like this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x492b8267

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+  82  Linux swap / Solaris

---

### Post by Duck2006 on 2008-03-29
That does seem strange. Do you have gparted loaded on your system? If not you can get it from Synaptic Package Manger, When you have it run it and it should show you as to where all the space is on your drive. Take a snap shot of it and post it here.

---

### Post by rkd on 2008-03-29
Well, whatever gparted might show, the fdisk clearly shows that the Ubuntu partition is at the start of the drive.  Unless the Windows installation was kind of odd (not placed at the start of the drive), it has been overwritten and is gone.

nagao88: Do you remember what answers you gave for the various questions it asked during the install of Ubuntu?

---

### Post by nagao88 on 2008-03-29
i just followed the standard installation procedure for dual boot ubuntu. i dont remember seeing anything about placing it at the start or end of a drive though, which now that you mention it, seems to make sense... 

so what do i do now? is it possible for me to run my recovery cd just on the other partition? or do i have to get a windows cd from somewhere...

---

### Post by rkd on 2008-03-29
The simplest thing, I think, is to make backup copies of anything on your Ubuntu installation that you want to keep, then put Windows back by running the recovery CD, then install Ubuntu again, taking extra care when you answer the questions during the installation to be sure you are telling it to keep Windows and just make some space available on the disk to use for Ubuntu.

I'm pretty sure you can't use the recovery CD to put Windows into another partition.  And even if you got a regular Windows install CD, people have had odd problems when they try to install Windows in a partition that isn't the first one on the disk.  That's why I say it probably is best to use the recovery CD, then reinstall Ubuntu.

I hope you have recent backups of your Windows data files so you don't lose much.  You'll have to reinstall any software you added to the system -- that won't be on the recovery CD if it came when you bought the computer.  If it is a recovery CD you made recently, then maybe your added software will be recovered, too.

---

### Post by nagao88 on 2008-03-29
i guess so - i won't lose any data cos i've just got this new hard disk after my previous one was shot. it's just the pain of doing about 5 installs in a week, and having to reconfigure everything again. 

so i have to put the ubuntu partition at the end of the disk?

---

### Post by rkd on 2008-03-29
You don't have to put the Ubuntu partition at the end of the disk.  If you want to leave some unused space, or put another Windows partition for data after the Ubuntu partition, that is okay.  It is just that people have had problems when the Windows boot partition isn't first.  (I don't know why they had problems. Windows ought to work okay if it isn't in the first partition, but at least sometimes it doesn't.)

Notice that Ubuntu needs at least two partitions -- the main one and the swap one.  It is possible to divide Ubuntu among more partitions, and some people advocate doing that, but at least while you are learning about Ubuntu, I think the extra partitions add more complexity than they are worth.

---

### Post by Duck2006 on 2008-03-30
> **nagao88 said:**
> after i removed my external hard drive, it looks like this:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x492b8267

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864        5106     1951897+  82  Linux swap / Solaris

>  but the ubuntu install only shows 40gb... how do i access the other 80gb which i seem to have partitioned away

512 * 14593 * 63 * 255 = 120.031511040Gb

As you see there does seem that some thing is missing, may be wrong.
It only show 40Gb as you said. Did you run gparted to see where the rest went?

---

### Post by rkd on 2008-03-30
Duck2006: Did you compose that post too hastily?  

Yes, fdisk reports the whole size of the disk correctly as 120 GB.  But if you look at the two partitions, one is about 39 GB and the other is about 1.9 GB, so there is a lot of unallocated space.

There is nothing wrong with that, of course, because fdisk doesn't display unallocated space. We don't know exactly how things got that way, but since nagao88 was trying to set up dual boot in the first place, it is understandable that only part of the disk was allocated to Ubuntu.  What went wrong to wipe out Windows and give Ubuntu only part of the disk is a small mystery, but probably not important.

---

### Post by marine63 on 2008-03-30
ducky THX this helped me alot :) (this is wat i meant last thread) thx

---

### Post by Paradoxfox93 on 2008-03-30
> **Duck2006 said:**
> When you just had windoze on your system did you have it installed on the first drive, and used the second drive for data?

I'm having the problems descirbed in this thread except i dont get an error message it semply reads 'starting windows' and hangs forever.

The setup for this computer was as described above.  I have XP on the first drive and data on the second.  moved the data to a USB and formated the seocnd drive for Ubuntu.  The computer I'm doing this on is not the one described in my sig.

---

### Post by Duck2006 on 2008-03-30
> **rkd said:**
> Duck2006: Did you compose that post too hastily?  

Yes, fdisk reports the whole size of the disk correctly as 120 GB.  But if you look at the two partitions, one is about 39 GB and the other is about 1.9 GB, so there is a lot of unallocated space.

There is nothing wrong with that, of course, because fdisk doesn't display unallocated space. We don't know exactly how things got that way, but since nagao88 was trying to set up dual boot in the first place, it is understandable that only part of the disk was allocated to Ubuntu.  What went wrong to wipe out Windows and give Ubuntu only part of the disk is a small mystery, but probably not important.

Yes i hat to go out and did do it a bit hastily. 
Sorry i forgot to put the other bit in to show the 41.998Gb all up.

---

