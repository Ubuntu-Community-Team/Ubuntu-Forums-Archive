---
title: "Grub Question"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Jer Engineer on 2008-02-24
In a nutshell, I have a HP DV9438ca, came with vista, I installed ubuntu on the second Hard Drive. Then after vista made me mad for the last time I installed XP over it on the first Hard Drive. This gave me a nice fresh XP that worked but killed my grub. So I used the ubuntu cd to "rescue" and fixed grub. Now I boot into ubuntu just fine but for the life of me cant get back into XP, I have searched far and wide for answers and have been to the grub site [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)


Here is my menu.lst

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3a00f0df-9fa0-4900-8966-c7cab93acb7d ro noapic irqpoll noirqdebug quiet
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3a00f0df-9fa0-4900-8966-c7cab93acb7d ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root


This entry automatically added by the Debian installer for a non-linux OS
on /dev/sda1
title Windows XP (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

#This is one thing I tried
#title Windows XP (loader)
#unhide (hd0,1)
#hide (hd0,0)
#rootnoverify (hd0,1)
#chainloader +1
#makeactive
#boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows Vista/Longhorn (loader)
root (hd0,1)
savedefault
makeactive
chainloader +1





and my sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdffa3cc

Device Boot Start End Blocks Id System
/dev/sda1 2 18401 147798000 1f Unknown
/dev/sda2 * 18402 19315 7338512 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc55952a8

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 13995 112414806 83 Linux
/dev/sdb2 13996 14593 4803435 5 Extended
/dev/sdb5 13996 14593 4803403+ 82 Linux swap / Solaris


Any Ideas besides reinstalling Ubuntu, I worked too hard to get it just how I like it :)

---

### Post by agim on 2008-02-24
What problems are you having exactly? Can you post error messages?
As far as a fix goes, have you checked out the super grub disk?

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

and some documentation

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by angrboda on 2008-02-24
Hi,
This might be the dumb question, but have you called up the grub-menu on startup (by pressing <Esc>)? Sorry for asking this but I have met people that where absolutely confused by the fact that Ubuntu hides the boot menu on startup (I can't blame them: the startup delay is a bit short by default, imho). And if that were all the problem, it would be silly not to have at least asked this. No offence intended

---

### Post by madsmaddad on 2008-02-24
I have XP and Kubuntu dual booting. Here is my Grub text: hope it helps.

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ba392444-d3ed-4626-a072-6ea81a9f9851 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ba392444-d3ed-4626-a072-6ea81a9f9851 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ba392444-d3ed-4626-a072-6ea81a9f9851 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ba392444-d3ed-4626-a072-6ea81a9f9851 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Jer Engineer on 2008-02-24
> **agim said:**
> What problems are you having exactly? Can you post error messages?
As far as a fix goes, have you checked out the super grub disk?

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

and some documentation

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Hi agim,

When grub loads and offers me the menu and I select XP to boot I recieve this error.

```
Error 12: Invalid device request
```

Error 12 (via grub manual): This error is returned if a device string is recognizable but does not fall under the other device errors.

I checked out your supergrub, looks interesting. I would like to use it as a last resort though. I should be able to dual boot without a disk.

-----------


> **angrboda said:**
> Hi,
This might be the dumb question, but have you called up the grub-menu on startup (by pressing <Esc>)? Sorry for asking this but I have met people that where absolutely confused by the fact that Ubuntu hides the boot menu on startup (I can't blame them: the startup delay is a bit short by default, imho). And if that were all the problem, it would be silly not to have at least asked this. No offence intended

No dumb question here Angrboda, Yes I have made some changes by doing as you said, Actually its the only way to get Ubuntu to boot on this laptop. I had to add "noapic irqpoll noirqdebug" to the end of my kernel string. Good question.

----------

> **madsmaddad said:**
> I have XP and Kubuntu dual booting. Here is my Grub text: hope it helps.
madsmaddad, The grub file is great but I need your "sudo fdisk -l" to go with it.



Thanks Everyone!

---

### Post by madsmaddad on 2008-02-24
sudo fdisk -l  (ell) I hope gives:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8db28db2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         522     4192933+   6  FAT16
/dev/sda2             523       15312   118800675    f  W95 Ext'd (LBA)
/dev/sda3           15313       19457    33294712+   c  W95 FAT32 (LBA)
/dev/sda5             523        5669    41343246    7  HPFS/NTFS
/dev/sda6            5670       14787    73240303+  83  Linux
/dev/sda7           14788       15312     4217031   82  Linux swap / Solaris

Disk /dev/sdb: 10.0 GB, 10005037056 bytes
16 heads, 63 sectors/track, 19386 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xf5faf5fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10636     5360512+   b  W95 FAT32
/dev/sdb2           10638       19386     4409496    5  Extended
/dev/sdb5           10638       19386     4409464+   b  W95 FAT32
peterm@peterm-Kdesktop:~$                      

The orig system was dos and XP. That is why SDA1 is Dos and SDA2 is XP. From Grub is I choose XP, I then get the choice DOS/XP. 

Peter M.

---

### Post by angrboda on 2008-02-24
Hi again,
> Error 12: Invalid device request
hmm, is the boot flag set for the device? I'm not quite sure (I do not use the Redmond-OS ;-) )but I think it needs to be set...

---

### Post by Jer Engineer on 2008-02-24
> **angrboda said:**
> Hi again,

hmm, is the boot flag set for the device? I'm not quite sure (I do not use the Redmond-OS ;-) )but I think it needs to be set...

Actually I'm not too sure. What is that and how do I check?

---

### Post by agim on 2008-02-25
The super grub disk, in addition to booting, can write to how it booted to your mbr. May be worth a shot.

---

### Post by angrboda on 2008-02-25
The boot flag is set to mark a partition as bootable. But I made a mistake here, overlooking the "*" in your fdisk -l output. 

> Device Boot Start End Blocks Id System
/dev/sda1 2 18401 147798000 1f Unknown
/dev/sda2 * 18402 19315 7338512 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.


It seems it is set. But  the "unknown" filesystem on /dev/sda1 does look strange. What is that? Could that be an artifact? /dev/sda2 seems defective: > Partition 2 does not end on cylinder boundary..

Something like this can happen, when you create a partition for XP from linux and then try to use it with Windows. The MS fdisk tool seems to draw the cylinder boundaries differently thus not ending partitions cleanly. I remember having killed a perfectly running Debian once by letting Microsofts fdisk re-partition the space I had reserved for Windows (back then, I kept both Systems on the same disk...). What happened was that the MS-fdisk expanded the Win-partition into the Linux partition.

If in your case somthing similar happened (and it looks a bit like it might have), it will not be quite as bad since you keep Ubuntu on a seperate disk. So at least that cannot be touched by Windows.
You might try to reunite the /dev/sda1fragment with the /dev/sda2 using gparted (only I am not sure that can handle ntfs -- maybe with ntfs-tools installed?) or if it is not too much of a pain simply re-install XP letting it repartition your first hdd. To get the grub back to be able to boot into Ubuntu again, you would then need to follow the instructions found here:

[http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")

or search the forum for other solutions to grub and the dual-boot problem.

Well, I hope this helps (even if it is not all good news... and a bit vague maybe)... I need to be off to work now :-( 
Good luck!
            Angrboda

---

### Post by Mustard on 2008-02-25
I remember reading somewhere that HP computers sometimes store stuff in a partition on the hard drive that has something to do with restoring windows.  I wonder whether this was the case with this HP system and whether that first partition related to this quirk of HP systems.

Here is an article on the subject that I googled up anyway...(keywords: hp partition recovery).
[http://www.pctechbytes.com/hprecovery.htm](http://www.pctechbytes.com/hprecovery.htm)

---

### Post by Jer Engineer on 2008-02-28
Hey guys,

I reinstalled XP on the first disk and when I did I wiped all partitions on it. I was trying to save the hp restore partition just in case I wanted vista back. So basically I fixed the problem by getting ride of the problem. Not really a solution but to the problem of not being able to boot with the configuration I had but it works now. Thanks for your help.

---

### Post by madsmaddad on 2008-04-11
How is it going? Have you resolved it?

---

