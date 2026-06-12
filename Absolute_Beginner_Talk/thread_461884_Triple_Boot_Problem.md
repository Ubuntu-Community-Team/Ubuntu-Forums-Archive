---
title: "Triple Boot Problem"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Ian Edmont on 2007-06-02
Hi,

I have XP installed, then installed Ubuntu and now Mandriva and now my grub menu doesn't have an entry to boot Ubuntu!!! :o(

Any ideas how and what to add to grub to get my Ubuntu entry back please?

Many thanks.

Ian Edmont.

---

### Post by Herman on 2007-06-02
Edit your mandriva grub menu wit a configfile boot entry for your Ubuntu partition something like this,
```
title  Ubuntu Feisty Fawn
configfile  (hd0,2)/boot/grub/menu.lst
```Where: Your Ubuntru partition happens to be /dev/hda3 or (hd0,2), please change that to whatever it really is for your set-up.
That should do the trick for you, and it allows Ubuntu to take care of updating its own kernel automatically with the debain automajic kernels list because you'll still be booting through Ubuntu's own grub menu.

Regards, Herman :D

---

### Post by STREETURCHINE on 2007-06-02
hi i have found it is always best to install all othjer os's then ubuntu.
i have zenwalk,sabayon,windows,fedora,then ubuntu on one hard drive,and ubuntu picks them all up

it saves editing the start menu:p

---

### Post by Abetorius on 2007-06-03
I've got similar problem, but this solution doesn,t work
Added to mandriva grub menu:

```
title  Ubuntu
configfile  (hd1,7)/boot/grub/menu.lst
```

and when I try to boot this option it returns error: Cannot mount partition.

My "fdisk -l" returns:
```
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551       10011    59930482+   f  W95 Ext'd (LBA)
/dev/hda5            2551       10011    59930451    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           2        4868    39094177+   f  W95 Ext'd (LBA)
/dev/hdb2            3446        4080     5100637+  83  Linux
/dev/hdb5               2        1785    14329948+   7  HPFS/NTFS
/dev/hdb6            1786        3445    13333918+   7  HPFS/NTFS
/dev/hdb7            4081        4802     5799433+  83  Linux
/dev/hdb8            4803        4868      530113+  82  Linux swap / Solaris

```

---

### Post by Herman on 2007-06-03
Hello Abetorius,
:D Yours looks like it's on /dev/hdb7 if I'm guessing right.  /dev/hdb8 is your swap area according to that fdisk output and I guess probably /dev/hdb2 would be Mandriva?

Okay, don't forget that Grub likes to start counting from zero, so if you type (hd1,7) in your Grub entry that means it will be trying to boot /dev/hdb8, which would be your swap area.
You just need to change that to (hd1,6) and it should work.
```
title  Ubuntu
configfile  (hd1,6)/boot/grub/menu.lst
```
Try that and see what happens. :D

Regards, Herman :D

---

### Post by Abetorius on 2007-06-03
When You pointed it out it seems obvious. Worked perfectly. Thanks.

---

### Post by Herman on 2007-06-04
Okay, good Abetorius, thanks for letting me know. Happy booting!
Regards, Herman :D

---

### Post by pospam on 2007-06-11
Hi all:
I currently double boot windows XP and Ubuntu I would like to
triple boot Xp-Ubuntu-Test distro.
I just want to be able to have the option to install other linux distros to give
them a test drive (i know that I can use liveCds but I rather try them at full speed
for a truthful comparison) without messing up my ubuntu install.
How should I Partition my hard disk?
THis is my current setup:
Partition 1-ntfs-Xp
Partition 2-ext3-home (for Ubuntu)
Partion 3-ext3- / (for Ubuntu)
Partition 4- swap.

What changes should I do and what partitions should I add in order to be able to triple boot?
Thanks for help.
P.

---

### Post by Herman on 2007-06-11
Hello pospam,
>  THis is my current setup:
Partition 1-ntfs-Xp
Partition 2-ext3-home (for Ubuntu)
Partion 3-ext3- / (for Ubuntu)
Partition 4- swap.

What changes should I do and what partitions should I add in order to be able to triple boot? I'm sorry but if those are really your partition numbers then you have used up all your primary partitions and you can't make any more partitions on that hard disk.
You could buy another hard disk and add it to the machine if your computer is a desktop. :D

Maybe those are not your real partition numbers, if you can post the output from 'sudo fdisk -lu' or a screencap from GParted, I or someone could probably help you better. 

We can have up to four primary partitions per hard disk, and they always occupy the partition numbers 1,2,3 or 4.
If we want to create more than four partitions we can make one of our four partitions a 'extended' partition, we can only have one extended partition per hard disk, and it can be number 1,2,3 or 4. Then inside the extended partition, we can have many logical partitions, those alway start numbering from 5 and upwards, regardless of whether the numbers 1 to4 are all occupied.

Well actually if you have the disk space maybe you could use [GParted -- LiveCD]("http://gparted.sourceforge.net/") to delete your swap area and then resize your other partitions smaller, make an extended partition number 4, then a new swap area number 5. You would need to edit /etc/fstab to tell it your swap area is number 5 now. Then you could install another distro in the free space you created. :D It can share the same swap area, and if you really want to it can even share the same /home, so you'll only need about 2 GB or so of free space, 5 GB would be more comfortable. I prefer to keep all my installs separated though personally.

You might be able to get the new distro to install its IPL for grub to the bootsector of its own / partition and then boot Ubuntu and add a configfile entry as shown in the post above. If it boots with Lilo you would need a chainloader entry instead. Refer to this link,  [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems").
You should at least make a copy of [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to make sure you will be able to cope with any initial booting hiccups until you get time to sort them out properly. :D
If you can't get the new distro to install Grub or Lilo to its own bootsector and it insists on the MBR, don't worry, just let it do what it wants. The MBR can be written to an infinite number of times. Just re-install Ubuntu's Grub IPL to it later, or configure the new system to boot Ubuntu, or both. :D

All the best, have fun multi-booting,
Regards, Herman :D

---

