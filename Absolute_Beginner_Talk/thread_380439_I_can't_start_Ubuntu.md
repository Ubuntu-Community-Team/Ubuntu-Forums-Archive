---
title: "I can't start Ubuntu"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by mesmerize on 2007-03-09
I have two hd's, one with Ubuntu and the other with XP.When I boot from the hd I get this message:
Booting 'Ubuntu, kernel 2.6.15-28-amd64-generic'
root (hd1,1)
Error 22: No such partition
If I boot from the installation CD and choose boot from first hard disk it begins to load Ubuntu and I can enter the user and password but then it freezes loading Windows manager.

---

### Post by Cannonade on 2007-03-09
I am also getting the Error 22 problem, but I can boot into ubuntu using the super grub disc ok. I also have the configuration Windows on master, ubuntu on slave but ubuntu drive set as first boot priority in the BIOS.

---

### Post by mesmerize on 2007-03-09
Both hd's are SATA so there is no master or slave, but I'll try to boot from the second hd.

---

### Post by mesmerize on 2007-03-09
I get the same, doesn't mind from which hd I boot.

---

### Post by Cannonade on 2007-03-10
Can you try getting into ubuntu from the super grub disc? This was how I solved my problem.

Get super grub disc from:
[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Or use it on the Ultimate Boot CD from:
[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

And if you can get into Linux, open a terminal and type in:

sudo gedit /boot/grub/device.map

and post what you get.

And then could you type in:

sudo gedit /boot/grub/menu.lst

And post the bits right at the end where the lines do not start with the '#' symbol.

PS. When you get the menu with 'Ubuntu, kernel 2.6.15-28-amd64-generic' highlight, press 'e' to edit. Then it will say root (hd1,1), press 'e' to edit and try typing in (hd0,1) and the press 'b' to boot and post the outcome. Thanks.

---

### Post by mesmerize on 2007-03-10
Super grub disk had not fixed the problem,  again Error 22: No such partition.I can get into Ubuntu booting from the recovery mode entry but it appears this message:
This program cannot start until you start the dbus system service.
It is strongly recommended you reboot your computer after starting messagebus.

The output of sudo gedit /boot/grub/device.map is
(hd0)	/dev/sda
(hd1)	/dev/sdb
and sudo gedit /boot/grub/menu.lst
title		Ubuntu, kernel 2.6.15-28-amd64-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-amd64-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

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

Now I'm going to edit the entry 'Ubuntu, kernel 2.6.15-28-amd64-generic' and change hd(1,1) to hd(0,1).

---

### Post by Cannonade on 2007-03-10
You will also have to change the mappings at the end of the menu.lst file where it lists Windows. Mine reads as following:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd1) (hd0)
map                (hd0) (hd1)
chainloader        +1

However, my configuration is ubuntu on the slave and Windows on the master, but I just change the BIOS boot order for it to boot from slave. Also, I have two IDE drives rather than SATA drives, and I think install is slightly different. But you will need to make sure that when you install Linux, the boot priority is set right in the BIOS and you install grub in the correct place. ie. to the master boot record of the Linux drive, not the boot partition. That's a mistake I made, I tried to install grub to /dev/hdb2 rather than simply /dev/hdb. But I think the outcome is a different error if that is the case.

I'm a little new to this stuff!

---

### Post by confused57 on 2007-03-10
> **mesmerize said:**
> I have two hd's, one with Ubuntu and the other with XP.When I boot from the hd I get this message:
Booting 'Ubuntu, kernel 2.6.15-28-amd64-generic'
root (hd1,1)
Error 22: No such partition
If I boot from the installation CD and choose boot from first hard disk it begins to load Ubuntu and I can enter the user and password but then it freezes loading Windows manager.

Cannonade has given you some good advice and maybe a little more information about your system would be helpful.
You can boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

Are you able to boot Windows from grub?

If you decide you want to try restoring Windows IPL code to your Windows drive mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The Super Grub Disk, recommended by Cannonade, can also restore your mbr.

If you can get your Windows drive to boot independently of grub, you might want to read over this option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by mesmerize on 2007-03-11
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      198546   100067152+   f  W95 Ext'd (LBA)
/dev/sdb2          198547      240156    20971440   83  Linux
/dev/sdb3          240157      310101    35252280   83  Linux
/dev/sdb5               2      193763    97656048    b  W95 FAT32
/dev/sdb6          193764      198546     2410600+  82  Linux swap / Solaris

I can't boot Windows from grub.I get this message:
Booting 'Microsoft Windows XP PRofessional'
root (hd0,0)
Filesystem type unknown,partition type 0xf
savedefault
makeactive

Error 12:Invalid device requested.

---

### Post by john_spiral on 2007-03-11
To get Windows XP working:

Edit your 'Windows XP' entry in the menu.lst file to look exactly like the following (as suggested by Cannonade). 

title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

The 'map' lines are very important.

Please come back to us with your results.

---

### Post by confused57 on 2007-03-11
Your system "should" boot just the way you currently have it set up...what is on the large FAT32 logical partition on sdb, I don't know if this might cause a problem, with the extended partition being partition #1 or not?

I would recommend you restore your Windows mbr, using the Super Grub Disk, or the link I gave you earlier:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
this way you would still be able to boot Windows independently of grub, while you're trying to get Ubuntu working.  Once you're able to get Windows booting properly, you could switch your Ubuntu drive to the sda position, set bios to boot first to sda, & try reinstalling Ubuntu to sda...I don't know if it'll make a difference to try the i386 version, instead of the AMD64.  I really don't know if the FAT32 extended partition being partition #1 might be causing a problem.
Here's the link I gave in my first reply for setting your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by mesmerize on 2007-03-11
I've changed the menu.lst adding the lines that cannonade posted and now I can boot into Windows using grub, but still I can't boot into Ubuntu.
Concerning the FAT32 partition in sdb, I really don't know what is it. Probably I did something wrong when I was partitioning the disk. How can I remove it?

---

### Post by confused57 on 2007-03-11
You might want to boot up the live cd, open a terminal, post the contents of your menu.lst:

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sdb2 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

and your device.map:
```
gksudo gedit /mnt/ubuntu/boot/grub/device.map
```

I don't know if your FAT32 extended partiton is affecting your ability to boot Ubuntu, it would be easier to reinstall Ubuntu, rather than try to rearrange the partitions currently on your Ubuntu drive.
If you decide to reinstall Ubuntu, you might want to read over this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Make sure to turn the "boot flag" on for your root partition.

You might want to make a copy of the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it's a great partitioning tool and it might show if your current root partition has the boot flag turned on...I'm not sure if you can set the boot flag from the gparted live cd or not.

---

### Post by mesmerize on 2007-03-12
This is the contents of menu.lst:
title		Ubuntu, kernel 2.6.15-28-amd64-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-amd64-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-28-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-28-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map (hd1) (hd0)
map (hd0) (hd1)
chainloader	+1

and device.map:
(hd0)	/dev/sda
(hd1)	/dev/sdb

I've downloaded the gparted liveCD and the boot partition doesn't have any boot flag, so I've turned it on and rebooted but still I can't get into Ubuntu. Maybe the only thing I could do is reinstalling.

---

### Post by confused57 on 2007-03-12
Do you actually get a grub menu when you boot first to your sdb Ubuntu drive?  If you do, try here what Cannonade suggested, highlight your Ubuntu entry, press "e" to edit, change your root from (hd1,1) to (hd0,1), then press "b" to boot.

If you're not getting a grub menu booting first to your sdb drive, you could install grub to the mbr with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
if you do have to install grub to your sdb Ubuntu drive, set your hard drive boot sequence the same that it was in bios when you installed Ubuntu...I assume Windows sda drive was set to boot before sdb when you installed...then select setup (hd1), instead of setup (hd0), following the instructions in the "howto", to install grub to sdb mbr.

Once grub is installed to your sdb mbr, then change your boot order to boot sdb first, then try the first suggestion above...post back if this works.
If it doesn't then reinstalling may be necessary.

---

### Post by mesmerize on 2007-03-12
There's a grub in the sdb hard disk too.Editing and changing the root from hd(1,1) to hd(1,0) let me boot ubuntu but it crashes again loading windows manager, so I'm going to do a reinstall. A couple of questions:Where have I to install grub (sda or sdb)? and if I install grub in sda, the boot flag of root partition of sdb has to be set on?
Thanks for your patience.

---

### Post by confused57 on 2007-03-12
> **mesmerize said:**
> There's a grub in the sdb hard disk too.Editing and changing the root from hd(1,1) to hd(1,0) let me boot ubuntu but it crashes again loading windows manager, so I'm going to do a reinstall. A couple of questions:Where have I to install grub (sda or sdb)? and if I install grub in sda, the boot flag of root partition of sdb has to be set on?
Thanks for your patience.
Don't reinstall yet, we may be able to get your Windows to boot.

---

### Post by confused57 on 2007-03-12
I wanted to send you the previous quick reply, so you don't start reinstalling just yet...I have a few things you can try:

Change your device.map:

```
gksudo gedit /boot/grub/device.map
```

to

```
(hd0) /dev/sdb
(hd1) /dev/sda
```

then add an entry to the bottom of your menu.lst to boot Windows:
```
gksudo gedit /boot/grub/menu.lst
```

add this entry to the very bottom of your menu.lst:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

see if these changes will allow you to boot into Windows from grub, booting first to your sdb drive.

If these changes work, then the only other thing you need to do is change this line in menu.lst:
# groot=(hd1,1)
to
# groot=(hd0,1)

You'll need to change all your Ubuntu entries in menu.lst to root (hd0,1).

Added: I won't be around for a couple of hours, so I won't be able to followup immediately...someone else should be able to help you, if I'm not available...good luck.

---

### Post by mesmerize on 2007-03-12
I think I don't explain clearly in my last post what was the fault. Windows boots perfectly right now. I'm using it to write this. The problem is that Ubuntu crashes after entering the user and password.It stops loading window manager and I have to reset the computer.
I'll wait to reinstall Ubuntu. I had some programs that I'd like to keep.

---

### Post by confused57 on 2007-03-12
> **mesmerize said:**
> There's a grub in the sdb hard disk too.Editing and changing the root from hd(1,1) to hd(1,0) let me boot ubuntu but it crashes again loading windows manager, so I'm going to do a reinstall. A couple of questions:Where have I to install grub (sda or sdb)? and if I install grub in sda, the boot flag of root partition of sdb has to be set on?
Thanks for your patience.
Yes, I misunderstood.  You explained your situation clearly, I just read it too quickly and automatically assumed you meant Windows crashed, instead of Ubuntu's window's manager.

When you reinstall, go ahead and set your sda to boot before sdb & install grub to sda mbr...what I'd do differently(don't know if it'll make a difference) is to set your first partition on sdb as your root partition...you probably know this, but you can only have 4 primary partitions on a hard drive.  One of the primary partitions can be an extended partition, in which you can have many logical partitions...the extended partition is automatically created if you set a partition as logical.  Ubuntu(root, home, swap, ext 3 data) can be installed on logical partitions.

There may be something else going on with your system that you may need to designate boot parameters to boot your kernel, or possibly using the Desktop i386 version would make a difference, if reinstalling still doesn't work.
Here's some information about boot parameters:
[http://www.ubuntuforums.org/showpost.php?p=2279812&postcount=56](http://www.ubuntuforums.org/showpost.php?p=2279812&postcount=56)

Personally, I would do as I've suggested earlier...restore Windows IPL code to your sda mbr, so you can boot your Windows drive independently of Ubuntu if you needed to.  Once you get Windows booting on sda...change your bios boot order to boot sdb before sda, install Ubuntu to sdb, installing grub to sdb...then use grub to boot Windows from sdb.  Set up this way, you would always be able to boot Windows by booting first to sda.

It's your choice, but at least you have some options to consider.

---

### Post by mesmerize on 2007-03-14
Finally I've got Ubuntu running. I've followed your advice, formatting sdb, creating new partitions and eliminating grub from sda. Again, I've had problems booting both Ubuntu and Windows, but reading all the thread has helped me to resolve it. Maybe I've learned something about grub and booting :) 
Thanks again for your help.

---

### Post by confused57 on 2007-03-14
> **mesmerize said:**
> Finally I've got Ubuntu running. I've followed your advice, formatting sdb, creating new partitions and eliminating grub from sda. Again, I've had problems booting both Ubuntu and Windows, but reading all the thread has helped me to resolve it. Maybe I've learned something about grub and booting :) 
Thanks again for your help.

Good to hear you got everything working, and I'm sure you learned a lot about how grub works & how to repair your Windows IPL code on your Windows drive...now, you can boot to Windows by changing your hard drive boot order in bios, if you ever needed to.  Thanks for the update.

---

