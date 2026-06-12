---
title: "Tried to dual boot Vista and Ubuntu, now can't get back into Vista"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by revolver4ever on 2006-10-13
Hi all

This is my first time trying Ubuntu and I'm loving it but I needed to get back into Windows for something and saw no option for it in GRUB.

Here's what happened:  I was dual booting XP and Vista on the same hard drive.  Never used XP again so decided to wipe that partition and try out Ubuntu.  Put in the Live CD, wiped the XP partition using Gpartition, and created two new partitions for Ubuntu install and swap.

Install went fine, everything is working ok.  But when I start up my computer, Ubuntu is loaded right away.  I can press esc to get into that Kernel choosing screen (386 or 686..I think) but no Vista there.

So I looked at the guides here and browsed some forums, and tried to add this entry to my boot list.  I did this:

  gksudo gedit /boot/grub/menu.lst

and added 

title  Microsoft Windows Vista Beta 
root   (hd0,4)
savedefault
makeactive
chainloader +1

to the bottom of the document.  I got the (hd0,4) number by listing all my partitions and seeing which ones had Unknown as file type.  Two did, hd0,2 and hd0,4 and I've tried both.

When I try to launch from that entry, I think it says Unsupported file system or Unknown file system and won't let me boot into Windows.

I don't know what else to do.  Here's my partition list:

Swap partition - /dev/sda3 Filesystem: Memory Swap     Flags: boot

Partition 1 - /dev/sda1  Filesystem: Extended 3    Flags:  none

Then there is an Extended partition /dev/sda2 under which there is Partition 5: /dev/sda5   File system:  NTFS.  The flag on the extended partition is lba.  So this is the one my Vista install is supposed to be on.  I can access it through Ubuntu and use all my files there, but can't boot.  

I've read the guides and really am kind of lost at this point.  Any help?  Thanks a bunch in advance!

---

### Post by catlett on 2006-10-13
It might be that the XP version of NTDLR (the windows bootloader) was booting vista. Grub doesn't boot windows. It passes the boot to windows bootloader (ntdlr) and that does the actual boot. If XP was installed first and you added vista, most likely XP was the system that contained the bootloader for XP and vista.
Just to make sure you are using the correct partition, post the output of this ```
sudo fdisk -l
```
Did you move vista or was it always installed on a logical partition?

---

### Post by JayTee on 2006-10-13
Setting up a Dual Boot with Vista is a bit differnt. Vista uses a new boot process instead of ntloader and doesn't play well with Ubuntu when Vista is installed on the primary or first partition. Here's what I had to do to get Vista to work. 
Install Vista first. Setup two partitions. Install Vista on the second partition. 
Install Ubuntu from the LiveCD but when you get to the partion manager point delete the first partition and then hit the back button and choose the option to use available space. This will create your boot partition and swap partition for Ubuntu and install the GRUB boot manager. When the install is done and you can boot into Ubuntu successfully then open a terminal window to edit your GRUB menu.lst file
sudo gedit /boot/grub/menu.lst
scroll to the end of the menu.lst file and after the section that says
END DEBIAN AUTOMATIC KERNELS LIST
Add the following statements after this line.
title		Windows Vista RC1
root		(hd0,1)
makeactive
chainloader +1
Save the menu.lst file and reboot. Choose the Vista option to test.
NOTE: This is only for installing Ubuntu and Vista on the same hard disk 
where the disk is the primary or first disk in the system.
Also, if you want to let Vista load as the default count the number of Ubuntu boot options and Vista then subtract 1 from that total and add the line Default # where number is that number you just calculated. The first boot option is always 0 so if Vista is the fifth option in the file the statement would be: Default 4

---

### Post by revolver4ever on 2006-10-13
Here's the output of sudo fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        5789       12748    55906200   83  Linux
/dev/sda2           12749       30400   141789690    f  W95 Ext'd (LBA)
/dev/sda3               1         532     4273258+  82  Linux swap / Solaris
/dev/sda4             533        5788    42218820   83  Linux
/dev/sda5           12749       30400   141789658+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

As far as moving Vista, I never moved if anywhere.  Originally I had 2 partitions, one with XP and one for data storage.  I installed Vista on that second partition.  Then I wiped XP and installed Ubuntu on that partition.  Kind of dumb but I had no external hard drive at the time and couldn't back up as much data as I wanted.

---

### Post by JayTee on 2006-10-13
can you post your menu.lst file contents from GRUB? The number of partitions you have is a bit confusing. Do you have two linux distros installed?

---

### Post by revolver4ever on 2006-10-13
I only have Ubuntu 6.06. The only thing I did is install the updated Kernel for my dual core pentium processor.  The last entry is what I tried to add.  

Here's the menu.lst file:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title  Microsoft Windows Vista Beta 
root   (hd0,4)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by catlett on 2006-10-14
I don't know if you are still searching for an answer but I thought I would post again. First, thanks to JayTee for the input about Vists using a new bootloader. I did not know about that.
Second, unless you have another hard drive that wasn't plugged in when you ran sudo fdisk -l, you do not have Vista on that drive. There are only linux partitions on that drive, no window partitions.
Here is the breakdown of your drive.
> /dev/sda1   *        5789       12748    55906200   83  Linux
That is your first primary partition. It has the boot flag so it is most likely your Dapper installation.
> /dev/sda2           12749       30400   141789690    f  W95 Ext'd (LBA)
This is your second primary partition. It has been turned into an extended partition. It holds the logical partition /dev/sda5 which is formatted as swap (swap is virtual memory for your system. Whereas windows uses a swap file, linux uses a swap partition.
> /dev/sda3               1         532     4273258+  82  Linux swap / Solaris
This is your third primary partition. It is formatted as swap space.
> /dev/sda4             533        5788    42218820   83 Linux
This is your fourth primary partition. It is formatted as a linux type of filesystem. Most likely ext3 (although it could be ext2, gparted would have given you the option of ext3 by default) This is most likely an empty partition with nothing on it.
> /dev/sda5           12749       30400   141789658+  82  Linux swap / SolarisThat is the logical partition that is inside your extended partition /dev/sda2.

So sorry to say but Vista is not on (hd0,4) If the data was important, you can find some commercial apps to get your data back but if you do not care, delete all your partitions after /dev/sda1.
Them make /dev/sda2 a 1gb swap.
Make  /dev/sda3 a large ntfs partition for vista
Then make /dev/sda4 a 10gb fat32. That is optional but it is convenient if you have the extra space. Vista and ubuntu can read and write to fat32 so that partition can be used as a transfer partition for files you want to share between the 2 OSs

---

