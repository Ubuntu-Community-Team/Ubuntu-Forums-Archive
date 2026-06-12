---
title: "Ubuntu kicks serious ***, need help with GRUB"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Super Nade [OCF] on 2007-07-13
[CENTER][FONT=Comic Sans MS][SIZE=6]***[COLOR=Red]Problem solved. Mods please mark this thread as RESOLVED!![/COLOR]***[/SIZE][/FONT]
[/CENTER]
 

Folks,

After experiencing the Black Screen of death during installation, I managed to set up an Ubuntu A64 box. I am very impressed by the speed and swiss army knife qualities of Ubuntu. Heck, I am so happy that I junked Windows from my X41 laptop and put 7.04 on it. :)

To make things even more sweet, I have my X1900XTX and the TV Wonder VE setup and running smooth. Now, I have one last problem before I declare Victory... i.e dual booting to Windows on my Desktop PC.

My config is as follows:
20Gb IDE has Ubuntu.
36Gb Raptor has Windows
36Gb Raptor has Games
300 Gb  NTFS SATA has other data 
200 Gb  NTFS SATA has more data
DVD RW is SATA

In the BIOS, the Ubuntu IDE is first Boot device. 

fdisk -l output:
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       24792   117218272+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1370    11004493+   7  HPFS/NTFS
/dev/sdb2            1371       36483   282045172+   f  W95 Ext'd (LBA)
/dev/sdb5            1371       36483   282045141    7  HPFS/NTFS

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        2434      859477+   5  Extended
/dev/hda5            2328        2434      859446   82  Linux swap / Solaris

``````
goonda@goonda:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  5.9G   11G  36% /
varrun                502M  116K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  144K  502M   1% /proc/bus/usb
udev                  502M  144K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   39M  464M   8% /lib/modules/2.6.20-16-generic/volatile
/dev/sdd1              35G   20G   16G  56% /media/G A M E S
/dev/sdc1              35G   16G   20G  45% /media/O S
/dev/sdb5             269G   68G  201G  26% /media/S T O R A G E
/dev/sdb1              11G  8.1G  2.5G  77% /media/Backup from Laptop
/dev/sda2             112G   56G   57G  50% /media/ M R I & movies
/dev/sda1              79G   78G  877M  99% /media/ M E D I A

```With this information, I looked up a few resources and edited the grub menu file. It does not work. I'm not sure how to proceed from here. The /media/OS i.e /dev/sdc1 is my XP boot drive.


/boot/grub/menu.lst output:
```
itle           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=afd90fbc-77a9-46f4-85c2-e8b381b19025 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=afd90fbc-77a9-46f4-85c2-e8b381b19025 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=afd90fbc-77a9-46f4-85c2-e8b381b19025 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=afd90fbc-77a9-46f4-85c2-e8b381b19025 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# Windows XP added by me
title           Windows XP Professional
root            (sd2,0)
savedefault
makeactive
chainloader     +1
map (hd0) (sd2)
map (sd2) (hd0)

```Can somebody please help me? :(

Thank you!

S-N

---

### Post by Cappy on 2007-07-13
Maybe
```

# Windows XP added by me
title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

You can easily mess around with it on the GRUB menu selection screen if you press "e". For instance, you can press "e" and change "(hd1,0)" to "(hd2,0)" and then try booting again.
More instructions on that here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

If you still get a "black screen of death" with Ubuntu add " nosplash" on the end of your boot line for Ubuntu.

---

### Post by Super Nade [OCF] on 2007-07-13
> **Cappy said:**
> Maybe
```

# Windows XP added by me
title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

You can easily mess around with it on the GRUB menu selection screen if you press "e". For instance, you can press "e" and change "(hd1,0)" to "(hd2,0)" and then try booting again.
More instructions on that here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

If you still get a "black screen of death" with Ubuntu add " nosplash" on the end of your boot line for Ubuntu.

Thank you! I will try it out. I'm confused about GRUB numbering. Should it be sd instead of hd? Also, from the fdisk and outher output, how can I translate the coordinates of my OS drive to the Grub format?

Edit#
Black screen solved. I had to install ATI drivers after starting from the Alternate CD. :)

---

### Post by confused57 on 2007-07-13
You could see how your hard drives are designated in your device.map:
```
gedit /boot/grub/device.map
```

If your Window's drive is indeed (hd2), then this entry should work:
```
title           Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader     +1
```

Here's an excellent guide explaining how grub works:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Super Nade [OCF] on 2007-07-17
[COLOR="Red"]PROBLEM SOLVED!
[/COLOR]

Thank you sir! It works like a charm!

Here is the ending part my new config file with Windows appended to it:

```
# Windows XP
title           Windows XP Professional
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
makeactive
chainloader +1

```

---

### Post by LaRoza on 2007-07-17
You have to mark it, go to reply, and click the "Advanced" link/button.

---

