---
title: "Dual Boot GRUB does not recognise XP"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Orizon on 2007-06-27
Hello,

I have just installed Windows XP and Ubuntu 7.04 on separate partitions. I am absolutely new to Linux and Ubuntu so don't really know what I am doing. My problem is that I cannot get XP to boot, my computer boots straight into Ubuntu and when access the GRUB menu by pressing 2 (or whatever it was), XP is not listed.

The partitions look like this:
/dev/sda1            6105        7296     9574740   83  Linux
/dev/sda2              27        6104    48821535    f  W95 Ext'd (LBA)
/dev/sda5              27        1242     9767488+   7  HPFS/NTFS
/dev/sda6            1243        5983    38082051    b  W95 FAT32
/dev/sda7            5984        6104      971901   82  Linux swap / Solaris

sda1 is where I installed linux and sda5 is where I installed XP. sda6 was supposed to be a data partition accessible by both OSs. When specifying the partitions I wasn't sure whether they should be primary or logical partitions. So I chose primary for sda1 and logical for the rest (I did not choose either for the XP partition because it already existed). I also have an unallocated section at the beginning of my hard drive of about 200MB which was an accident.

If anyone could help that would be great. Ubuntu otherwise seems great so far!

---

### Post by jackiecanev2 on 2007-06-27
can you post your /boot/grub/menu.lst?

---

### Post by Orizon on 2007-06-27
Hello,
contents of /boot/grub/menu.lst is:
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6b4dc29-c481-402b-be79-002650b5e213 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6b4dc29-c481-402b-be79-002650b5e213 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

Thank you.

---

### Post by Orizon on 2007-06-27
Sorry I missed the last line of /boot/grub/menu.lst:

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by jackiecanev2 on 2007-06-27
try adding this to your /boot/grub/menu.lst 

since i'm not sure what you did with your partitions, exactly, it could be hd0,1... etc.
(hd_,_) refers to the physical disk drive, and the partition number, respectively.

title Windows XP
root (hd0,2)
makeactive
chainloader +1

---

### Post by Orizon on 2007-06-27
menu.lst is read only for me. When I right-click and click 'Properties' and then 'Permissions' it says only the 'Owner' has permission to read and write (all others only have read permission).

I am using the account I created in the installation process but I can't seem to edit menu.lst.

---

### Post by logos34 on 2007-06-27
> **Orizon said:**
> menu.lst is read only for me. When I right-click and click 'Properties' and then 'Permissions' it says only the 'Owner' has permission to read and write (all others only have read permission).

I am using the account I created in the installation process but I can't seem to edit menu.lst.

Try this:

Open a terminal and type:

**gksudo gedit /boot/grub/menu.lst**

Now you have superuser priviledges to edit files.

Add to the bottom a windows entry:

> title		Windows XP
root		(hd0,4)
makeactive
chainloader	+1

This points to your XP partition on sda5.

---

### Post by Orizon on 2007-06-29
Thank you.

I reinstalled both windows and XP before I saw your message but gksudo does let me edit menu.lst so that could have saved me quite alot of time. I am sorry not to have been able to try it out.

When I installed ubuntu for the second time, it recognised XP and everything works now, which is good!

---

### Post by Adramelech on 2007-06-29
i think windows needs to be on the first partition of the hard drive

---

