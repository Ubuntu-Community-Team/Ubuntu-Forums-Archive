---
title: "Update keeps over-writing grub's menu.lst"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by vavroom on 2007-06-08
Ok, well, this, per se, is not a problem, it's the natural behaviour when a kernel update is sent down.  I realise that.

But!  I need root to be found like so:

root		(hd0,5)

Yet, at every single update that involves a kernel change (or so it seems), it reverts to 

root		(hd0,4)

It's not a major drama, I just have to stop grub from booting, edit the start line, resume booting, then go in and edit /boot/grub/menu.lst

Not a major drama, but it's starting to really tick me off! :)

Any idea how I can fix it so it keeps using the right partition ?

Thanks in advance.

---

### Post by Inxsible on 2007-06-08
It seems strange that it would list the wrong partition as the root. Coz it wouldnt start up. You dont have multiple instances of Linux installed, do you?
The only thing that I can think of right now is the zero-based, 1-based confusion. Grub's disk partition reader is 0-based. So 4 is really the 5th partition 5= 6th partition. But your update seems to increase the number :confused:
Can you post your ```
sudo fdisk -l
```and your ```
gedit /boot/grub/menu.lst
```

---

### Post by vavroom on 2007-06-08
> **Inxsible said:**
> It seems strange that it would list the wrong partition as the root. Coz it wouldnt start up. 

I'm running dual boot, so always get the grub menu first.  After a kernel update, it doesn't go any further than the grub menu until I edit the boot partition to (hd0,5).

> **Inxsible said:**
> You dont have multiple instances of Linux installed, do you?

No, not unless upgrading using the upgrade feature installed two versions of Ubuntu.

> **Inxsible said:**
> The only thing that I can think of right now is the zero-based, 1-based confusion. Grub's disk partition reader is 0-based. So 4 is really the 5th partition 5= 6th partition. But your update seems to increase the number 

No, it seems to *decrease* it.  It boots with (hd0,5), it doesn't work with (hd0,4).  The kernel update changes it from 5 to 4.

Thanks for having a look :)

fdisk:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4972    39937558+   7  HPFS/NTFS
/dev/sda2           30137       30401     2128612+  92  Unknown
/dev/sda3            4973       30136   202129830    f  W95 Ext'd (LBA)
/dev/sda5            4973        6374    11261533+   7  HPFS/NTFS
/dev/sda6            6375        8286    15358108+  83  Linux
/dev/sda7            8287        9561    10241406   83  Linux
/dev/sda8            9562        9816     2048256   82  Linux swap / Solaris
/dev/sda9            9817       30136   163220368+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7296    58597087+   f  W95 Ext'd (LBA)
/dev/sdb5               2        7296    58597056    b  W95 FAT32

```

Menu.lst:
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=3cbaf448-ceaf-4a67-9bb5-eb558b09f716 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Inxsible on 2007-06-08
> No, it seems to *decrease* it. It boots with (hd0,5), it doesn't work with (hd0,4). The kernel update changes it from 5 to 4.
D'oh :oops: I am glad i dont teach math !!

---

### Post by Inxsible on 2007-06-08
Well your fdisk and menu.lst look in order. Like you said it should be (hd0,5) = sda6. 
As to why the kernel update changes it to (hd0,4), the only thing that comes to mind is,
your /dev/sda3 is an Extended drive. Therefore sda5, sda6 etc are logical partitions within sda3.

Now, I am shooting in the dark here, but I think, it sees that your root is under an Extended partition and then simply assumes that the 1st Logical partition (sda5) is your root, which is equivalent to (hd0,4) because the grub's disk partitions are 0-based.

---

### Post by vavroom on 2007-06-08
Ok, that makes some sense.  How do I go about changing it?  Any easy way to test it before moving partitions around?

---

### Post by Inxsible on 2007-06-08
> **vavroom said:**
> Ok, that makes some sense.  How do I go about changing it?  Any easy way to test it before moving partitions around?

Nothing you do in either OS is going to matter because the grub sees the drives before them. You can get rid of the sda5 -which is NTFS and move it to the end of the sda6. This means you should back up your sda5 if you have data on it. Also moving around partitions and spaces could result in weird things happening.

If it happens only infrequently, you can simply live with it. Or if you must change it, I would say atleast be prepared to re-install your Ubuntu.

GParted can actually help you move partitions around. Its not known to give problems, but you might never know !

---

### Post by Inxsible on 2007-06-08
sda5 also doesnt seem to be a very big partition. Do you really need it where you have it ?

Also wondering what sda2 is, again a small partition with Unknown file system

---

### Post by vavroom on 2007-06-08
> **Inxsible said:**
> sda5 also doesnt seem to be a very big partition. Do you really need it where you have it ?

I keep my games' ISO disks there.  I *could* move that elsewhere and do away with the partition.

> **Inxsible said:**
> Also wondering what sda2 is, again a small partition with Unknown file system

Ah, yes, no choice on that one, it's the IBM built in partition with all the system recovery stuff.

---

### Post by confused57 on 2007-06-08
You need to change the line with #groot:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by vavroom on 2007-06-08
confused57!  Thank you.  That seems like such a simple answer and I've stared at that part of menu.lst many, many times.

Thank you :)

---

### Post by confused57 on 2007-06-08
> **vavroom said:**
> confused57!  Thank you.  That seems like such a simple answer and I've stared at that part of menu.lst many, many times.

Thank you :)
Glad to help...it's not something a new user would know to look for, over time you'll pick up small tips & tricks to configuring your system...Herman's site has some great info on bootloaders, & much more/

---

