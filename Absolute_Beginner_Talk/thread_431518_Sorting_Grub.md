---
title: "Sorting Grub"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by SnowLinux on 2007-05-03
My questions concern the Edubuntu 7.04 desktop install.

I already have Win98SE on a primary DOS FAT32 partition.

I’ve created two ext partitions for a “\” , and  “\home” and also a swap  partition. I made “/” a primary partition and “\home” a logical partition.

When through to the install screen having selected all the options for partitions and prior to hitting install button, I selected the partiton (hd0,0) where Windows is to install Grub. 
Should this be  (HD0.1) where Edubutu will install to ?   

On completion of install and rebooting, PC boots straight to Edubuntu with no grub menu to select Windows – problem to sort!

Can any one copy and paste the lines of script that should be in 
menu.lst file in the /boot/grub folder please for a Windows / Edubuntu (or Ubuntu) dual boot system please.

thanks

---

### Post by Skrynesaver on 2007-05-03
Could you post the output of 
```

sudo fdisk -l

```
This will give people a better idea of what is where and what it might be called

---

### Post by SnowLinux on 2007-05-03
well for command   sudo fdisk -l,

I get the following return. Where do I go from here?

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         389     3124611    b  W95 FAT32
/dev/hda2             390        1003     4931955   83  Linux
/dev/hda3            1004        1690     5518327+   5  Extended
/dev/hda5            1004        1617     4931923+  83  Linux
/dev/hda6            1618        1690      586341   82  Linux swap / Solaris

---

### Post by Churnd on 2007-05-03
What do you actually have in your /boot/grub/menu.lst?  Most menu.lst files have a sample Windows entry in them.

---

### Post by Skrynesaver on 2007-05-03
Your /boot/grub/menu.lst should look a bit like the following but with comments
```


default          0
timeout         3
hiddenmenu

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

root (hd0,1) 
kernel /boot/vmlinuz root=/dev/hda2  ro 3 
 
 
title Win98SE
rootnoverify (hd0,0) 
chainloader +1 
makeactive 
boot 
 
```

---

### Post by mikewhatever on 2007-05-03
Can you please post from the terminal the output of 
> cat /boot/grub/menu.lst

Is it called the terminal in Edubuntu?

---

### Post by Duck2006 on 2007-05-03
Change

timeout         3
hiddenmenu

To

timeout        10
#hiddenmenu

In your menu,lst, you will be able to see the menu

---

### Post by SnowLinux on 2007-05-04
Since posting this issue for getting the dual boot sorted,
I've discovered that the HDD I'm using has an error problem with the LBA .
Once I've got the HDD changed and tried to install again I'll post
the Sudo command outputs as requested.

Many thanks for the feedback I've had so far.

---

### Post by SnowLinux on 2007-05-05
I've reinstalled all, Win98 and Edubuntu on a different HDD 
and now have the dual boot I wanted.

My menu.lst file has been written - 

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e1542974-7abf-412a-a917-684131032fad ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e1542974-7abf-412a-a917-684131032fad ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1


************************************
Point of interest that folks may wish to note!
I normally intall Windows 98 SE in to a directory called Win98.
On the install I've just done, I left it default at Windows and grub 
has managed to configure the dual boot -  so it seems leave Windows 98 installs as defult!

Any chance the Ubuntu team could update Grub to allow for custom
named Windows 98 SE installs? 
By the way, how do I get a graphical way for configuring boot options in Edubuntu?

thanks for all the above advice folks

---

