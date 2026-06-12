---
title: "GRUB did not auto-detect my XP partition - help?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Simon Flavelle on 2007-04-22
Hi all,

Since I installed Ubuntu (6.06, the mailed one) I have not been able to access my Windows Drive. I made a partition on the same drive, but it doesn't recognise at all. The installation (and my Windows partition too) is on my 200GB Slave drive (hdc). Could this one fact be what is causing the problem? And can someone tell me how to re-add XP to the boot menu?

Thanks in advance,

Simon Flavelle

---

### Post by ajmorris on 2007-04-22
> **Simon Flavelle said:**
> Hi all,

Since I installed Ubuntu (6.06, the mailed one) I have not been able to access my Windows Drive. I made a partition on the same drive, but it doesn't recognise at all. The installation (and my Windows partition too) is on my 200GB Slave drive (hdc). Could this one fact be what is causing the problem? And can someone tell me how to re-add XP to the boot menu?

Thanks in advance,

Simon Flavelle

to add xp to the boot menu, go to /boot/grub and edit menu.lst as root. ( can be done through a terminal or the GUI, in the terminal just type : sudo gedit /boot/grub/menu.lst)

then under the "## ## End Default Options ##" section add to the bottom of all the rest of your entries this:

title		Windows XP
root		(hard disk and partition number, i.e. (hd0,0) for first hard disk first partition) (to find the partition number in a terminal type sudo fdisk -l and find the ntfs partition type.) ( also grub starts from 0 so if it is first hard disk and first partition (/dev/hda1 or /dev/sda1 from fdisk -l then it would be (hd0,0))
savedefault
makeactive
chainloader +1

e.g for me when i had windows it was:

title    Windows XP
root     (hd0,1) *(ubuntu was my first partition, windows my second)*
savedefault
makeactive
chainloader +1


hope that wasn't too confusing.

---

### Post by Simon Flavelle on 2007-04-22
> **ajmorris said:**
> root		(hard disk and partition number, i.e. (hd0,0) for first hard disk first partition) (to find the partition number in a terminal type sudo fdisk -l and find the ntfs partition type.) ( also grub starts from 0 so if it is first hard disk and first partition (/dev/hda1 or /dev/sda1 from fdisk -l then it would be (hd0,0))Okay, so in Windows the drive XP and Ubuntu are installed on would be considered the "D" drive, so would that be (hd1,#)?

---

### Post by 5-HT on 2007-04-22
> **Simon Flavelle said:**
> Okay, so in Windows the drive XP and Ubuntu are installed on would be considered the "D" drive, so would that be (hd1,#)?

Could you please post the output of ```
sudo fdisk -l 
```That command will show your partition tables which is needed in order to determine which disk and partition  xp is on.

---

### Post by Simon Flavelle on 2007-04-22
> **5-HT said:**
> Could you please post the output of ```
sudo fdisk -l 
```That command will show your partition tables which is needed in order to determine which disk and partition  xp is on.
Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1192     9574708+  83  Linux
/dev/hda2            1193        1247      441787+   5  Extended
/dev/hda5            1193        1247      441756   82  Linux swap / Solaris

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hdc1               1       12988   104326078+   7  HPFS/NTFS** <-- So in this case it would be (hd1,0)?
/dev/hdc2   *       12989       24509    92542432+  83  Linux
/dev/hdc3           24510       24792     2273197+   5  Extended
/dev/hdc5           24510       24792     2273166   82  Linux swap / Solaris

---

### Post by ajmorris on 2007-04-22
hdc is usually 3rd hard disk, but it looks like in ur case that is is your second, so yes it is (hd1,0)

---

### Post by 5-HT on 2007-04-22
After appending the following to the end of /boot/grub/menu.lst, can you boot in XP properly?
 ```
title        Microsoft Windows XP 
rootnoverify        (hd1,0)
savedefault
makeactive
chainloader    +1 
```To append it to the file:
1. Open a terminal
2. Backup your old menu.lst 
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup 
```3. Open up the file with write privileges, paste the above (at the end of the file), and save
```
 sudo gedit /boot/grub/menu.lst 
```On reboot, grub should now list XP as an option for booting.

HTH

---

### Post by aeroz on 2008-02-27
i am having the same problem with this... I can't boot my windows OS on boot loader... please help me what should i put on the menu list... 

here is my menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d278bbda-cb6b-4008-a9e1-74ea0729b662 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d278bbda-cb6b-4008-a9e1-74ea0729b662 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP
root	 	(sda5,0) 
savedefault
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST


and here is my fdisk -l information....  

Device Boot      Start         End      Blocks               Id               System
/dev/sda2               1           9728    78140128+   f            W95 Ext'd (LBA)
/dev/sda5            3825       9728    47423848+   7            HPFS/NTFS
/dev/sda6               1           486      3903700+     83          Linux
/dev/sda7             487        972      3903763+      82        Linux swap / Solaris
/dev/sda8             973        3824    22908658+   83                     Linux


thank you so much... 

aeroz

---

