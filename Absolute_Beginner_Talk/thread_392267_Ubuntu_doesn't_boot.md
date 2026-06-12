---
title: "Ubuntu doesn't boot"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Bungo Pony on 2007-03-24
I've tried installing Ubuntu 3 times onto my 20 gig hard drive, and it doesn't boot. I've tried installing it with the Windows hard drive plugged in, unplugged, set as a master, and set as a slave, and it will not boot at all. The installation of the Edgy live CD seems to go fine, but when it reboots, I get a disk error.

I tried re-formatting the hard drive in Windows and it works fine.

Anybody have any ideas?

---

### Post by taurus on 2007-03-24
What kind of disk error do you get when you try to boot it?

---

### Post by Bungo Pony on 2007-03-24
The PC cannot find a system disk. Basically the same message when you leave a data floppy in when you boot your PC

---

### Post by taurus on 2007-03-24
So you set that 20GB with Ubuntu on as a single master drive.  Where did you install GRUB bootloader?  And did you by any chance moving harddrives around after you installed Ubuntu?

---

### Post by Bungo Pony on 2007-03-24
Yes, I tried setting it as a single drive. I let GRUB install into the default location (/hdr?)

---

### Post by Bungo Pony on 2007-03-24
Nobody knows?

---

### Post by bulldog on 2007-03-24
Yes somebody will know,but need a little more information in what you did.

Boot the live cd and leave all the disk you want to use connected.
Perform the next command in a terminal,and copy the output to the forum,we'll take it from there.
```
sudo fdisk -l
``` it's a lower case L not a one.

---

### Post by Bungo Pony on 2007-03-24
Here it is:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         892     7164958+  27  Unknown
/dev/sda2   *         893        3442    20482875    7  HPFS/NTFS

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2392    19213708+  83  Linux
/dev/hdb2            2393        2498      851445    5  Extended
/dev/hdb5            2393        2498      851413+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by bulldog on 2007-03-24
Ok,no errors as it seem.
I presume you'll boot from the sda disk normally,but I recommend to boot from the IDE [hdb] disk.

Grub will be installed by default on the IDE disk unless you told it otherwise.
If you let it install on (hd0) like the default,it should be installed to the hdb disk.
In that case you should be able to boot ubuntu,but not windows.

So make the IDE disk the master boot device in your BIOS and boot and tell me if you see the GRUB menu.

---

### Post by Bungo Pony on 2007-03-24
I've already tried that and I just get the non-system disk error

---

### Post by bulldog on 2007-03-24
Your hardware is recognized by the live cd so there a re no errors.
Look in your BIOS if both hdd's are listed,and set the IDE disk as the master boot device.
If GRUB isn't installed on this disk we have to do it again.

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Now GRUB will be installed to the IDE disk.
Boot from this disk and let me know if GRUB is loading and you can get into ubuntu,but not into windows.

---

### Post by Bungo Pony on 2007-03-24
This is what came back:

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.l
st "... succeeded
Done.

---

### Post by bulldog on 2007-03-24
I have a little question though,your linux disk seems ok,but what's on the first sda1 partition,the one with UNKNOWN behind it?

---

### Post by Bungo Pony on 2007-03-24
The first 20G is formatted NTFS for Win2k. The other 140G partition isn't formatted.

---

### Post by bulldog on 2007-03-24
And you're still able to boot win2k if you boot from the sda disk?
It's a little strange to me it's installed on the second partition instead of the first one.

---

### Post by Bungo Pony on 2007-03-24
Win2k boots fine (although I'm having driver issues - hooray for 16 colors!)

---

### Post by Bungo Pony on 2007-03-24
I don't know how the hell I got the second partition done that way. Do you think I should re-format and re-install win2k?

Wait, that shouldn't affect the other drive since I tried installing Ubuntu without the SATA drive plugged in. My PC also has a boot menu built into the bios, so that kinda makes selecting the hard drive easier

---

### Post by bulldog on 2007-03-24
Yes I know it won't affect ubuntu,I only try to figure out why you get the boot error.

If in the menu.lst your windows is listed and it can't find it again,you'll get some errors reinstalling GRUB.

But anyway,GRUB is reinstalled so you can try to boot from the hard disk  and have a look if GRUB comes up with the menu.
If so we can handle the errors if there are any :)

---

### Post by Bungo Pony on 2007-03-24
Same boot disk failure :(

---

### Post by bulldog on 2007-03-24
There seems to be an error with the disk,but the live cd sees it perfectly.
I'm sorry but if it's a hardware failure,I can't help you.

If you disconnect the sata disk you're still unable to boot from the IDE disk?
Is the disk  listed in your BIOS ?

---

### Post by Bungo Pony on 2007-03-24
> If you disconnect the sata disk you're still unable to boot from the IDE disk?
Correct.

> Is the disk listed in your BIOS ?
Yes it is. Windows can also see it, but Windows runs really sluggish when I have it connected (at least when its formatted with exp3)

BTW, this PC is brand new - out of the box yesterday. The hard drive is a bit old though.

---

### Post by Bungo Pony on 2007-03-24
I'm currently installing it on a 6G hard drive I have laying around, just so I can eliminate the possibility of the hard drive being the problem. I'll let you know how it goes.

---

### Post by Bungo Pony on 2007-03-24
So guess what? It boots off the 6G hard drive :-P ](*,) 

Now I'm wondering why the hell my 20G drive is shot (or is it a hardware compatibility problem?) I'll figure that out in a bit. It boggles my mind because that's what I was running on before I got my new PC. 

My next problem is my onboard ethernet card (stay tuned).

But thanks for all your help!

---

