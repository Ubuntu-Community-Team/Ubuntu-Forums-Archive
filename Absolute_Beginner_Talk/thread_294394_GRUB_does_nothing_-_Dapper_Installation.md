---
title: "GRUB does nothing - Dapper Installation"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by *BERT* on 2006-11-06
Hi, hope someone can help me with my problem. 

I've been trying to dual boot dapper with windoze xp using the NTLDR. 

I've been following the instructions on this webpage:
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

I installed GRUB to the bootable root partition like it says and went through the process of copying the boot bin file to the windows partition and adding it to the boot.ini but when i reboot and choose my ubuntu option all i get is a blank screen with GRUB written in the top left corner and a blinking cursor. 

I've done a lot of googling the past day or so and checked a lot of fixes but i haven't managed to find one that works. 

My setup is 
hda1 - ntfs windows xp
hdb1 - fat32 
hdb2 - ext3 ubuntu
hdb3 - swap

I've checked /boot/grub and it contains these files:
default
device.map
e2fs_stage1_5
fat_stage1_5
jfs_stage1_5
menu.lst
minix_stage1_5
reiserfs_stage1_5
stage1
stage2
xfs_stage1_5

My menu.lst configuration looks like this:

> 
## ## End Default Options ##

title	Ubuntu, kernel 2.6.15-26-386
root	(hd1,1)
kernel	/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro quiet splash
initrd	/boot/initrd.img-2.6.15-26-386
savedefault
boot

title	Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root	(hd1,1)
kernel	/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb2 ro single
initrd	/boot/initrd.img-2.6.15-26-386
boot

title	Ubuntu, memtest86+
root	(hd1,1)
kernel	/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

#

I've looked in /boot and the files: 
vmlinuz-2.6.15-26-386
initrd.img-2.6.15-26-386

are in there. 

I have a bootable linux recovery disk which i've been using to check things out with. 

Any suggestions?

---

### Post by mo79 on 2006-11-06
You might want to try [this]("http://ubuntuforums.org/showthread.php?t=275728") method. It's how I did it.

---

### Post by subzero79 on 2006-11-06
With the dapper CD boot in live mode. Go to console.

sudo grub
root (hd1,1)
setup (hd0)
quit

reboot

Once logged inot your dapper install fix the /boot/grub/menu.lst

add the following lines to the end if they are not already there

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by *BERT* on 2006-11-07
Hi subzero79, won't that install GRUB to my MBR?

---

### Post by subzero79 on 2006-11-07
> ***BERT* said:**
> Hi subzero79, won't that install GRUB to my MBR?

Of course. ntldr doesn't load linux. Grub does, also grub can point to the root partition of windows and then start ntldr. Why do you want to use ntldr to load linux?:-k

---

