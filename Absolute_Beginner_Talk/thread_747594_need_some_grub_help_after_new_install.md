---
title: "need some grub help after new install"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by b0b138 on 2008-04-06
So I've been messing around with gutsy for awhile, and decided to wipe it out and try the latest hardy beta. The install seemed to go fine but it won't boot into anything.  grub error 21 (i think, not sure at this moment. right now im on a live session)

I'm duel booting xp and ubuntu.

I have 3 80GB drives. As windows sees it theres my c: drive and my mirrored d: drive. c: is the one partitioned with ubuntu.

In gparted it shows sda and sdb as my mirrored drives. sdc has both installs. sdc1 is ntfs. sdc2 is ext3. sdc3 is extended and under that is sdc5 swap.

Here is the important part of menu.lst

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=f7f2431c-80c0-4649-ab90-291a8d6275e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=f7f2431c-80c0-4649-ab90-291a8d6275e2 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Anyone got any ideas to get this booting? I'll reboot in just a sec to get the error code.

---

### Post by louieb on 2008-04-06
Just wondering are you getting the GRUB menu?
What type of drives (IDE/PATA or SATA)?
Also go ahead and post the content of /boot/grub/device.map?
Something confused the installer just have figure out what.
Did you change the boot order in BIOS since you made the install?

---

### Post by b0b138 on 2008-04-06
Yes I am getting the GRUB menu.

sda and sdb are ide. thats my mirrored set. sdc is sata 

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

I changed the boot order before the install to boot off the cd, but havent changed it since.

---

### Post by louieb on 2008-04-06
When you get the grub menu press **c  to get a grub command line. **

And lets have GRUB tell you where it is. 

```
find /boot/grub/stage2
```

Should be able to use what it returns in the root statement of the Ubuntu entry in /boot/grub/menu.lst. That should get rid of the error 21.

---

### Post by b0b138 on 2008-04-06
well i made some progress.  I changed the root (hd2,1) to (hd0,1) and its booting.

i tried (hd0,0) for xp but that didnt work. Maybe something to do with the map lines, I didnt have those lines on the gutsy install :confused:

---

### Post by louieb on 2008-04-06
The map lines are to fake windows out into thinking its on the 1st drive in the boot order.  Go ahead a comment them out and see what that does. 

Just a shortcut you can** press e on the XP entry **and edit the entry there. It temporary so once you find what works. Just change /boot/grub/menu.lst to make it permanent.

---

### Post by b0b138 on 2008-04-06
find /boot/grub/stage2   gave me hd0,1

I got into xp. I changed root (hd0,0) and commented out 
map (hd0) (hd2)
map (hd2) (hd0)

But now Im really confused. According to gparted, my xp and ubuntu are installed on /dev/sdc

wait, now im MORE confused. gparted now says xp and ubuntu are on sda, and sdb and sdc are my mirrored drives.

Does hardy have some raid or fakeraid stuff built in?

---

### Post by bumanie on 2008-04-06
Please supply the output of > sudo fdsik -l (that's a lower case L).

---

### Post by b0b138 on 2008-04-06
```
rob@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf485f485

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8963    71993848+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            8964        9689     5831595   83  Linux
/dev/sda3            9690        9729      321300    5  Extended
/dev/sda5            9690        9729      321268+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c99dd69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c99dd69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9725    78116031    7  HPFS/NTFS
rob@ubuntu:~$ 

```

---

### Post by louieb on 2008-04-06
> **b0b138 said:**
> ...But now Im really confused. According to gparted, my xp and ubuntu are installed on /dev/sdc..

Don't know about the raid detection. But GRUB probes BIOS to make a guess at the boot order and says sda is 1st sdb is 2nd...  When there a mix of sata and ide drives in the computer sometimes grub-install  doesn't get it right.  Thats why you had problems with the  Hardy beta install.

GParted when run from a live CD does much the same thing. Thats why I asked about you going into BIOS and changing the boot order around.  

:guitar:Going to guess myself that somehow the drive with the Ubuntu install go changed from last in the boot order to 1st.  The device.map file kinda shows that too.   And thats my wild as guess of the day.

---

### Post by bumanie on 2008-04-06
> In gparted it shows sda and sdb as my mirrored drives. sdc has both installs. sdc1 is ntfs. sdc2 is ext3. sdc3 is extended and under that is sdc5 swap.
fdsik indicates that your drives are set up somewhat different to what you've said above. According to fdisk, sda has windows and ubuntu, whilst sdb and sdc are windows drives that I assume are your raid drives (have little experience with raid). xp is at (hd0,0) and ubuntu is at (hd0,1) and swap is at (hd0,4) on the first drive. Why the drives are so different to what you have quoted I can't say. But the partition designations I have put above are what fdisk shows. I have to go now, hope you sort it out and hope what I have indicated will give you some help.

---

### Post by b0b138 on 2008-04-06
> **bumanie said:**
> fdsik indicates that your drives are set up somewhat different to what you've said above. According to fdisk, sda has windows and ubuntu, whilst sdb and sdc are windows drives that I assume are your raid drives (have little experience with raid). xp is at (hd0,0) and ubuntu is at (hd0,1) and swap is at (hd0,4) on the first drive. Why the drives are so different to what you have quoted I can't say. But the partition designations I have put above are what fdisk shows. I have to go now, hope you sort it out and hope what I have indicated will give you some help.

Yeah, thats why I got more confused. Im 99% sure earlier it did. :lolflag:  Im also 99% sure on my gutsy install it showed it the same way. Now that its says sda has xp and ubuntu, that makes more sense to me cause thats the drive listed in bios as the first and only hdd to attempt to boot from.

Well hey, at least its working now :)

Many thanks to both of you, you've been a great help.  cheers  	:biggrin:

---

