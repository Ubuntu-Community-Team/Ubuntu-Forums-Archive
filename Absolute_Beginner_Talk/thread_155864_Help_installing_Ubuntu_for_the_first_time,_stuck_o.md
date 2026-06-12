---
title: "Help installing Ubuntu for the first time, stuck on Grub"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by oldbucsfan on 2006-04-05
Hello,

I am installing Ubuntu for the first time and the install instructions seem to say nothing about how to use or set up this part.

I followed the installation instructions and got to the part where it ejects the disk and reboots.  It then comes up with grub loading.  Then grub just sits there waiting for me to tell it something.  What am I supposed to do here?  How do I use grub to boot Ubuntu?

---

### Post by dermotti on 2006-04-05
You should have a grub menu where you can select (with your arrow keys) what kernel you want to boot. You should select the first option.

---

### Post by oldbucsfan on 2006-04-05
[QUOTE=dermotti]You should have a grub menu where you can select (with your arrow keys) what kernel you want to boot. You should select the first option.[/QUOTE]

No, I don't see that.  I get a text interface with a "grub>" prompt.  I type in "boot" and it says "Error 8: Kernel must be loaded before boot".

---

### Post by dermotti on 2006-04-05
**edit: **Did you remeber to take the CD out?

---

### Post by oldbucsfan on 2006-04-05
Yes, I took it out before the reboot.  It does the same thing every time I try to boot from that hard drive.  I have Windows on this hard drive and it boots fine (not using grub for this hard drive).

---

### Post by sn123 on 2006-04-05
[QUOTE=oldbucsfan]Yes, I took it out before the reboot.  It does the same thing every time I try to boot from that hard drive.  I have Windows on this hard drive and it boots fine (not using grub for this hard drive).[/QUOTE]
could you post the contents of your menu.lst (if any) and devices.map files?
```

grub> cat \boot\grub\menu.lst
grub> cat \boot\grub\devices.map 

```
if devices.map doesn't work replace it with device.map.

or use ex2fs ([http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)) to view these files in XP.

S

---

### Post by oldbucsfan on 2006-04-05
device.map--->>
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


menu.lst---->>
default		0

timeout		3

hiddenmenu

title		Ubuntu, kernel 2.6.12-9-amd64-k8 Default 
root		(hd2,0)
kernel		/boot/vmlinuz root=/dev/sdc1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8 Default (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz root=/dev/sdc1 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8 
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8 root=/dev/sdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8 root=/dev/sdc1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-k8
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin  
boot

---

### Post by sn123 on 2006-04-05
[QUOTE=oldbucsfan]device.map--->>
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


menu.lst---->>

title		Ubuntu, kernel 2.6.12-9-amd64-k8 Default 
root		(hd2,0)
kernel		/boot/vmlinuz root=/dev/sdc1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8 Default (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz root=/dev/sdc1 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8 
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8 root=/dev/sdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-k8 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8 root=/dev/sdc1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-k8
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin  
boot[/QUOTE]
On the grub prompt execute these commands one after the another and see if you can boot into linux or post any errors that are displayed:
```

grub> root (hd2,0)
grub> kernel /boot/vmlinuz root=/dev/sdc1 ro quiet splash
grub> initrd /boot/initrd.img
grub> boot

```

---

### Post by oldbucsfan on 2006-04-05
tried to do
root (hd2,0)

and got this error
Error 21: Selected disk does not exist


So it seems that it isn't finding the hard drive that grub is loading from...?

---

### Post by oldbucsfan on 2006-04-06
I did a little more poking around and discovered that the drive with Ubuntu installed on it is actually (hd0,0) not hd2.  So, grub seems to be trying to use hd2 when hd0 needs to be used.  That is why I am unable to do anything.  Hard drive h2 doesn't even exist.  I am going to try to re-install again and see if there is a way to change this around.

---

### Post by Sutekh on 2006-04-06
No need to reinstall!!

The Ubuntu installation should be intact.  All that needs to be changed is the GRUB menu.  That's not too hard.

Please try the advice given by sn123.  But now you know that Ubuntu is on (hd0,0) use
```
grub> root (hd0,0)
grub> kernel /boot/vmlinuz root=/dev/sda1 ro quiet splash
grub> initrd /boot/initrd.img
grub> boot
```

If that boot into Ubuntu then you can change the menu.lst so that it looks in the correct location in future.

---

### Post by point on 2006-04-06
[QUOTE=oldbucsfan]I am going to try to re-install again and see if there is a way to change this around.[/QUOTE]

You should just edit your GRUB settings if the number of your HDD is the problem. While your computer is booting, press ESC to enter GRUB menu and click "e" to edit the Ubuntu entry (click "e" again to edit the lines).

---

### Post by oldbucsfan on 2006-04-06
[QUOTE=Sutekh]No need to reinstall!!

The Ubuntu installation should be intact.  All that needs to be changed is the GRUB menu.  That's not too hard.

Please try the advice given by sn123.  But now you know that Ubuntu is on (hd0,0) use
```
grub> root (hd0,0)
grub> kernel /boot/vmlinuz root=/dev/sda1 ro quiet splash
grub> initrd /boot/initrd.img
grub> boot
```

If that boot into Ubuntu then you can change the menu.lst so that it looks in the correct location in future.[/QUOTE]

I already tried that, but it didn't work either.  It seems that when grub was installed, it wrote hd2 to it's files.  So I could not use hd0, even with the code above.  I did get it to work in 2 ways.

1. Install without installing grub.  This works fine with using the code above, but it was a little buggy to try to install manually myself since I am not familiar with this OS.

2. Disconnect the other 2 hard drives while installing.  This worked fine as well, until I hooked the hard drives back to the computer.  It wouldn't boot anymore.

In conclusion, it seems that the installer from grub was reading the root hard drive as hd2 when installing since the other 2 hard drives appear before it in the partitioning section.  So, I think that this would also be fixed if I rearranged the order of my hard drives, but since I am using a RAID-0 config on the first 2, I don't want to rearrange them.  I installed Fedora and it seems to not have this same problem, so it should be fixable.

---

