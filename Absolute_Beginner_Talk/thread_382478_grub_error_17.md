---
title: "grub error 17"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by SharekhaN on 2007-03-12
Hi people . 

i had been using ubuntu 6.10 for over couple of weeks . i used to disconnect all my hdd and connect just my ubuntu hdd and work on it during the earlier stages . now i thought i would switch over to ubuntu as my primary OS and slowly migrate my data off my XP . SO i attached the hdd to my system . and started up the instalation . clean formatted the ubuntu drive and installed as defaults . 

When the system restarted , the system booted straight to win xp , and i didnt even see a grub . I selected my BIos boot options to boot off my samsung 40 gig hdd where ubuntiu was installed to see a grub but got an error 17 . I thought the groub was probabaly not installed properly on the boot partition . so i tried teh installation again and i this time specified the target of grub as sda , it took /dev/sda in the option . the installation again went smooth . restarted to see grub giving me option of win xp and ubuntu . xp booted with no issues but with ubuntu i still got the error 17 . 

please advice . 

This is the fdisk output from live cd . 

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       19457   103860225    f  W95 Ext'd (LBA)
/dev/sda5            6528       13054    52428096    7  HPFS/NTFS
/dev/sda6           13055       19457    51432066    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdc: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4669    37503711   83  Linux
/dev/hdc2            4670        4870     1614532+   5  Extended
/dev/hdc5            4670        4870     1614501   82  Linux swap / Solaris

```

This is my menu.lst dump 

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

---

### Post by SharekhaN on 2007-03-12
Ok , i tried booting to my other IDE drive from BIOS options , the 186 gb drive and it boots to linux , if i select it from grub , however it does not boot to XP . 

Now there has to be an easier way to do this ....:(

---

### Post by xyz on 2007-03-12
Try this for a start:
[17]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap5")
and
[Grub Errors]("http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting")

---

### Post by SharekhaN on 2007-03-12
Thanks for the reply , 

Problem seems to have solved . I set the BIOS to boot to the second ID drive strangely which does not have either XP or Ubuntu . It gives me the GRUB . now Ubuntu boots normally here , as i have mentioned . and XP now boots off the second of the two non linux os choices found on Grub . I wonder why it didnt map the comannds for the first choice as well . I found this as i was looking thru the menu.lst  file . 

Anyways thanks for the help community . Will be posting here as and when i need more help :)  .

---

