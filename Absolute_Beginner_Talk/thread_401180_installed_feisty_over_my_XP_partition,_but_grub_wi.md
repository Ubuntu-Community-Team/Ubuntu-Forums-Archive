---
title: "installed feisty over my XP partition, but grub will only show old Edgy"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by dr.drake on 2007-04-04
after playing for a long time, and never using windows at all, I decided to finally erase all microsoft from my computer. 
I erased XP and did a feisty install on that partition. BUT...

when booting, my boot options are just the same as before (see below), it still shows XP, and no feisty.??
how can I (automatically) edit grub to give me the option to boot into feisty and remove all evidence of ever having used windows???

I have 2 HDs, 5 partitions:
_**hdb**_:
hdb1  -  ext3 -  backups
**_sda_**:
sda1  -  ext3  -  feisty
sda3   -  fat32 - files
sda4   -  ext3  -  edgy
sda2   -  swap

I will change the fat into ext3 as soon as i get grub working properly..

my grub menu.lst:

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
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

```

I think i might also have messed up my fstab, trying to edit it manually..

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   	<type>  	<options>       		<dump>  	<pass>
proc            /proc           	proc    	defaults       	       	       	0       	0
/dev/sda1  	/media/sda1     	ext3    	defaults,umask=000		0		0
/dev/sda2  	/home/eric/fat32     	vfat    	iocharset=utf8,umask=000  	0    		0
/dev/sda3    	swap    		sw              				0       	0
/dev/sda4 	/               	ext3    	defaults,errors=remount-ro 	0       	1
/dev/hdb1  	/media/xtra     	ext3    	defaults,umask=000		0		0
/dev/hdd        /media/cdrom0   			udf,iso9660 user,noauto     	0       	0
/dev/hdc        /media/cdrom1   			udf,iso9660 user,noauto     	0       	0
/dev/           /media/floppy0  	auto    	rw,user,noauto  		0       	0
```

---

### Post by BarfBag on 2007-04-04
Which partition is the one with Feisty?

Edit - NVM.  Missed part of your post.

---

### Post by mac.ryan on 2007-04-04
I would guess (but it's just a guess, no warranty it is right!) that you MBR still points to the grub installed with Edgy (EdgyPartition/boot/grub) and not to the version installed with Feisty (FeistyPartition/boot/grub).

Hopefully Feisty recognised the existence of Edgy when installed, so I would suggest to copy the menu.lst from Feisty to Edgy (after backup of it!!) and 
see if this way you will get all the system recognised. Otherwise you might need to copy the bit of Feisty's file that points to Feisty boot into the Edgy file.

---

### Post by remmelt on 2007-04-04
Sups Eric,

Try to boot using the live cd, then run sudo update-grub. That should tell grub to detect which kernels and other os's you have installed, and update the menu.lst accordingly. Reboot, the feisty kernel should be listed in the menu.

You can also update the menu.lst by hand, but you would have to know which kernel is installed in the Feisty install... Look in the Feisty partition in the /boot folder, then just edit this:
```
title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot
```
and edit it. Your harddisc will probably be (hd0,0).
Put it UNDERNEATH the "### END DEBIAN AUTOMAGIC KERNELS LIST" line. Run sudo update-grub again so the MBR is updated, reboot. Now it's definitely there and if you didn't make any mistakes, you can boot to the Feisty install.

---

### Post by dr.drake on 2007-04-04
> **mac.ryan said:**
> I would guess (but it's just a guess, no warranty it is right!) that you MBR still points to the grub installed with Edgy (EdgyPartition/boot/grub) and not to the version installed with Feisty (FeistyPartition/boot/grub).

Hopefully Feisty recognised the existence of Edgy when installed, so I would suggest to copy the menu.lst from Feisty to Edgy (after backup of it!!) and 
see if this way you will get all the system recognised. Otherwise you might need to copy the bit of Feisty's file that points to Feisty boot into the Edgy file.

I would if I would be able to get into feisty in the first place.. :)
I'm trying Remmelt's option now.. eventhough I did sudo update-grub from the edgy side of things already

---

### Post by remmelt on 2007-04-04
Good idea though. Mount the Feisty partition and copy over the menu.lst to /boot.

update-grub, reboot.

---

### Post by dr.drake on 2007-04-04
right,
I had tried to mount the feisty partition before, which somehow only worked by doing it in gparted (?!) but then no files showed up.
the sudo update-grub from the live CD did nothing helpful, but I think now that feisty put a MBR on the hdb, while my bios wants to look in the sda, where the edgy MBR is.
so, I have booted into edgy again, mounted sda1 through gparted, and this time files did show up!
copied the grub menu.lst, and pasted it into the edgy grub file.

so I have rebooted again: and at least it shows all the right options, but..
when i choose the feisty one, I get a
- error 15: File not found
when I choose the edgy one, I get a 
- error 22: No such partition

press any key to continue..

ehrm... now I even lost edgy!!! ](*,) back on live cd

*edit:

I now unplugged the hdb, and are trying to instal on sda1 again, expecting the MBR to show up where it should now.
I will post again as soon as I get some results.

---

### Post by dr.drake on 2007-04-04
right, that worked. feisty that is, the rest i didn't test yet.
tomorrow I will try to use my 2nd harddrive, but now I need to get out of the house, catch a last ray of sunshine...

thanks anyway.

---

