---
title: "Dual Boot with Dual SATA drives"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by cdawley4 on 2008-02-06
Hi,

I am new to Ubuntu, but have used Fedora before.  I have 2 SATA hard drives in my system, an 80GB (WinXP) and 160 (Ubuntu).  When I installed Ubuntu, I unhooked my WinXP drive so my files wouldn't get messed up or Ubuntu install over them.  Once I got done installing Ubuntu, I hooked my my WinXP drive.  Now I am trying to dual boot WinXP and Ubuntu.  

Here is my fdisk -l

> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa53ea53e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000707e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19082   153276133+  83  Linux
/dev/sdb2           19083       19457     3012187+   5  Extended
/dev/sdb5           19083       19457     3012156   82  Linux swap / Solaris



Here is my menu.lst

> 
title		Windows XP Professional
rootnoverify	(hd0,0)
makeactive
chainloader	+1

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9f76b5df-f1aa-496f-b946-aa18bbb1c6d9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9f76b5df-f1aa-496f-b946-aa18bbb1c6d9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


Here is my fstab

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9f76b5df-f1aa-496f-b946-aa18bbb1c6d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0c7bbc4e-a1d4-4dba-bf25-c0c0f82a4243 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



If I change my rootnoverify line to (hd1,0), I get either Error 12 or Starting up and it hangs.  I have also added the map (hd0)(hd1) as well as map (hd1)(hd0) that fedora requires and that doesn't work.  I have changed my menu.lst file so many times, that I have forgotten what I have tried and what I haven't.

---

### Post by logos34 on 2008-02-06
try this:

> title Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

(*note space between parentheses in map lines)

Do NOT put windows stanza inside the 'DEBIAN AUTOMAGIC KERNELS LIST' section--move it to the bottom or else it will be deleted next kernel update.

You may also have to change /boot/grub/device.map for map commands to work:

> (hd0) /dev/sdb
(hd1) /dev/sda

To mount windows partition in linux:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by drubin on 2008-02-07
I am looking at doing the same thing only i am completly new to linux.

I have 2  250gig hard drives, currently the one has my windows OS on it. The other (nothing i mind loosing)

I have seen countless posts on dual booting with winows on a single hard drive...... but not sure where to look for multiple hard drives.

when during the install proccess does it ask what hard drive to install to? how would i know which one is which?

I am just scared i am going to over write my windows system. 
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu) 
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

Both nice to follow tuts, but non say a bout the dual hard drive things? (not sure if the sata part makes a differnce?)

---

### Post by sandysandy on 2008-02-07
have a look at this site for dual booting

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by phr0ze on 2008-02-07
Rubinboy:

If you plan to use the second drive, just boot the CD. Choose the install/live option at the first menu and load the system. At this point ubuntu has not touched your system, you can play with it and decide if you like it. Now on your desktop will be an install icon. Run this and go through the first few steps until you come to the disk selection. Pick the correct disk to install to, and click next. If at any time you don't feel comfortable prior to the final confirmation in the install, just reboot the computer and everything will be untouched.

Glad you are going to try it.

---

### Post by drubin on 2008-02-07
Thanks going to give that a try... 
I installed mythbuntu on a spare computer a while back. but but that didnt have 2 hard drivers  just wanted to make sure it wont over write things. :) 

Somthing that is stupid.

Doesnt this forum have email notifications? if it does where do you go to turn them on :) :)

---

### Post by drubin on 2008-02-07
Sorry again.

When will it ask me which OS i want to start up..... (Think it is called a boot loader?)

Or do i need to set that up? if so how?

---

### Post by sandysandy on 2008-02-07
> **rubinboy said:**
> Thanks going to give that a try... 
I installed mythbuntu on a spare computer a while back. but but that didnt have 2 hard drivers  just wanted to make sure it wont over write things. :) 

Somthing that is stupid.

Doesnt this forum have email notifications? if it does where do you go to turn them on :) :)

ubuntu will not overwrite windows unless u choose do so. when installing,  options are there on whether to use the entire hard disk or use custom partitioning or resize one of the partitions.

what can happen is that ur windows MBR can be overwritten. but generally grub takes care to include ur windows booting info so that u have choice at start up on which OS to boot into.

there is a utility called  super grub disk with which u can restore windows MBR if u so desire. u can also use ur win XP CD for the same purpose with fixmbr option.

regards

---

### Post by sandysandy on 2008-02-07
> **rubinboy said:**
> Sorry again.

When will it ask me which OS i want to start up..... (Think it is called a boot loader?)

Or do i need to set that up? if so how?

the boot loader is called GRUB. (other bootloader is LILO but that is rarely used now a days.)

regards

---

### Post by phr0ze on 2008-02-07
As stated, ubuntu normally sets the boot menu for you. You should not need to do anything else. 

yes the forums can email you. When you reply to a thread or make a post there is an option at the bottom just before the submit button the default option is to not subscribe. 

Here are the options you can choose.

**Thread Subscription**
**Notification Type:** 
Do not subscribe 
No email notification 
Instant email notification 
Daily email notification 
Weekly email notification

---

### Post by drubin on 2008-02-07
Thanks helped alot.

I was talking about the "default" option as under  user preferences but i found the link
[http://ubuntuforums.org/usercp.php](http://ubuntuforums.org/usercp.php)

---

### Post by drubin on 2008-02-08
Just another Quick question

How will i know what hard drive is what? in windows they are c:\ and e:\ but in linux they wont be??

So is there a way to check?

---

### Post by sandysandy on 2008-02-10
when installing see the hard disk size and note it down against the OS installed. otherwise go to Places----> Computer. all ur hdd are listed here. open each one and make a note of its contents.

sata drives would be listed as sda and IDE as hda. use sudo fdisk -lu for this.

Open Suse also has option to name partitions when installing, so that its easier to understand which hdd is what.

regards

---

