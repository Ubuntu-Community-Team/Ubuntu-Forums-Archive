---
title: "problems with GRUB"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by IceColdBD on 2006-07-06
I have been trying for the last few days or so to get 6.0.6 installed, and I keep running into problems with the bootloader. I have two hard drives, one SATA and one IDE, and I am installing Ubuntu on the IDE drive. I have XP on the SATA drive, going for a dual boot setup. So anyway, after trying many things, I finally tried to just load the GRUB onto a floppy and see how that would work. It doesn't. When I boot from the floppy, all I see is this:

GRUB _ 

Exciting. So, I also went ahead and installed GRUB on the IDE partition, and when I boot from that drive is get Error 22, which I think is some partition table error. I booted from the LiveCD and took a look at the menu.lst file and made some changes so that it loads Ubuntu from hd0,1, which is how GRUB has it mapped, and that made no difference. Last thing I tried was copy the first 512 bytes off the floppy I made, put it into a file and included that file in the boot.ini file for the Windows bootloader. Again, I see "GRUB _" and nothing more.

What is going on here? Is GRUB not able to recognize which partitions are which? I'm at a loss. Thanks in advance for any help.

-Josh

---

### Post by confused57 on 2006-07-06
From the Live CD, open a terminal and enter:
```
fdisk -l
```
The -l is a small "L".
(I don't think you have to preface the command with sudo using the LiveCD)

This should show your partition tables.

Also, here's a link to how I have my system set up(with 2 IDE drives):
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Sounds like you've been doing your homework, and maybe the above command will show something.  I've never personally dealt with SATA drives, but I've seen others have success dualbooting with combo SATA & IDE.

---

### Post by IceColdBD on 2006-07-06
Yeah, I've done the fdsisk -l command before. It doesn't really tell me anything that I don't already know. More than anything I just want to know what it means when GRUB just stops loading. When I see an error, I can at least proceed with some kind of troubleshooting, but when nothing happens at all, it's just frustrating. Why does it hang at 

GRUB _ 

ARRGGHH!

---

### Post by Jose Catre-Vandis on 2006-07-06
Please list your fdisk -l, then at least we can help from there :-)

---

### Post by IceColdBD on 2006-07-06
OK, here is the output of fdisk -l

```
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1            9425        9729     2449912+   5  Extended
/dev/hdc2   *           1        9424    75698248+  83  Linux
/dev/hdc5            9426        9729     2441880   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       36481    88237012+   f  W95 Ext'd (LBA)
/dev/sda5           25497       36481    88236981    7  HPFS/NTFS
```

And just for kicks, here is map.lst
```
(hd0)	/dev/hdc
(hd1)	/dev/sda

```

and menu.lst
```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
makeactive
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

So, just to rehash this a bit. I installed GRUB on the partition with ubuntu on it, so I can select that drive during startup and boot grub. But all I get is Error: 22. I changed the menu.lst file so that it says what it says now. Before I changed it the roots under the Ubuntu kernel boots said (hd0,1). The change did nothing. So, what shall I do?

---

### Post by catlett on 2006-07-06
I would change gears. If you can run the live cd, download gag.[http://gag.sourceforge.net/](http://gag.sourceforge.net/)  It is small, simple and good. You can either download and put it on a floppy or burn the iso to cd. Either one will make a boot disk.
When you boot to the disk it will ask you to install. Gag is small and fits entirely on the mbr, It does a simple job of boting you to a partition.
I would try that first. There have beenm alot of issues with Dapper and sata drives. I don't know if that is what is happening but it may be.
Try gag, I think you will like it.

P.S. If you want your windows botloader back (this will not let you boot to linux afterwards) Put in an XP (or win98) install disk and boot to it.Enter rcovery mode by entering "R" at the prtompt. You will eventuallt get to a command prompt. Enter ```
fixmbr
``` That will rewrite the master boot record and you will be able to boot to windows but not ubuintu

---

### Post by IceColdBD on 2006-07-07
Thank you catlett. GAG was a most excellent suggestion. Now I actually get to the GRUB menu, it doesn't just crap out immediately. But, I do still get an error. Error: 17, cannot mount selected partition. I changed the menu.lst file back so it is correct now, and keep in mind Ubuntu is on my IDE drive, not SATA. So, next course of action? GAG suggested LILO it looks like, should I install that? Or is there a quick troubleshoot for GRUB? Making progress people, thank you so much.

---

### Post by IceColdBD on 2006-07-07
Ok, new development. I decided I would try and completely reinstall Ubuntu (for the millionth time) but this time I simply disconnected my SATA drive and let it go. Lo and behold, it booted up just fine. Grub starts up and Ubuntu runs nicely. OK, so I reconnect my SATA drive, which has the GAG bootloader, and set it to be my first drive in the BIOS. However, if I try to boot Linux from GAG, I get the dreaded "GRUB _" and nothing more.

But I have found that if I change the boot priority through the BIOS, I can safely boot into either Ubuntu or Windows with no problem. The problem comes when I try to use GAG to boot into Ubuntu. What could be happening? Is Dapper just really unhappy about my SATA drive?

---

### Post by catlett on 2006-07-07
I don't know to tell you the truth. In theory everything should be fine but in practice there is an issue with dapper and sata. I spent a few posts trying to get grub working with people and it just wouldn't. The only common denominator was sata. That's why I didn't get into your menu and suggested gag.
Gag has had good results, I don't know why it is having issues. 
Lilo (lionux loader) was the first bootloader for linux systems. It's main drawback is you have to reconfigure it ant time you get a new kernel through an update. Grub automatically detects it and adds a menu option.

---

### Post by richbarna on 2006-07-07
>   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1            9425        9729     2449912+   5  Extended
/dev/hdc2   *           1        9424    75698248+  83  Linux
/dev/hdc5            9426        9729     2441880   82  Linux swap / Solaris
I noticed that instead of 3 partitions for Ubuntu :-
ext 3 boot
ext 3 home
swap
hdc1 is extended, you don't need an extended partition if you have less than four partitions. I had a problem with grub recognising two distros if one of them is inside an extended partition.

---

