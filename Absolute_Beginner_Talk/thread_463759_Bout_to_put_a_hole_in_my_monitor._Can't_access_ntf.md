---
title: "Bout to put a hole in my monitor. Can't access ntfs drive"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by pacguy on 2007-06-04
I just recently re-installed ubuntu again and am enjoying it all over again. I do have one confusing problem that is driving me up the wall and I can't for the life of me figure out why its happening. My second hd is ntfs and is mounted. I can access the files and bring them to my ubuntu hd with no problem. But the hd itself is listed as read only and I can't change it. I have gksudu natilus and tried to change the permissions. I change folder access but when I do it tells me that the hd is a read only drive. I then change file access to read-write but nothing happens. I also tried to access ntfs-config with alt-f2 but then it tells me I need admin rights even though I'm the only one on this computer.

If anyone has any suggestions I'd really appreciate it. My second hd is 200 gigs while my primary is 120 and I really can't afford to lose that much data.

---

### Post by voided3 on 2007-06-04
Get the "ntfs-3g" driver; that lets you read and write to NTFS drives. You get get it and the GUI frontend with synaptic (search ntfs-3g) or find it in add/remove programs. Good luck!

---

### Post by Inxsible on 2007-06-04
can you post the /etc/fstab ?

---

### Post by pacguy on 2007-06-04
Sorry I'm not to sure on how to run /etc/fstab I'm rusty on writing that in the terminal. What do I put before that.
I tried to run the ntfs config tool that add/remove programs installed. But when I did I got this.
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdd1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

No idea what that is. I used automatix to install the config tool so I have no idea whats up with that.

---

### Post by pappapump on 2007-06-04
Your problem is quite common really and so is the solution.
Find a windows PC and remount the drive from there then use the stop usb devices function to remove the drive, 
then when it is says its safe to remove the drive simply remove it from the usb slot and reinsert it when you start ubuntu and all will be well.
What happened is that windows didn't have the opportunity to close out the drive properly and release ownership.
When you eject properly, all that goes away and open permissions are restored.

---

### Post by pacguy on 2007-06-04
This is an internal drive and it has no USB connection on it. I've been able to mount the drive but can't the permissions.

---

### Post by pappapump on 2007-06-04
OH, my bad then, I must have misread the post.
Does your NTFS drive have a windows install on it?
If so, then you simply need to boot back to windows and r-click the drive in my computer and do a scandisk without the do a surface scan selected.
The problem you mentioned occurs with either a windows crash or a power button forced shutdown.

---

### Post by iqag1060 on 2007-06-04
pappapump is right if this is an external usb drive. If this is an internal drive in your dual-boot system, just exit Ubuntu and reboot in Windows and shut down cleanly.  Then reboot ubuntu and try again. 
You wrote in the beginning:
> I also tried to access ntfs-config with alt-f2 but then it tells me I need admin rights even though I'm the only one on this computer.

I'm guessing you figured this out, but you need to run "gksudo ntfs-config". The system will not let you make any potentially destructive or system-wide changes as yourself, you need to be acting as root (which is what sudo is allowing you to do.) This is a good thing.
Good luck.

---

### Post by iqag1060 on 2007-06-04
Sorry for the double information, looks like you two got there while I was typing.

---

### Post by pappapump on 2007-06-04
All I ever used was the ntfs configuration tool located in the add/remove programs list and set the mount point in that little text area, then clicked the read and write access boxes.
Works every time for me.
Either way, your error says you didn't do a clean shutdown of Windows, so you can go no further till you do that first, even IF you install an extra app in Ubuntu.

---

### Post by pacguy on 2007-06-04
I can't access windows any more because I wiped it completely when I installed ubuntu. Woot/oops
I added the ntfs config tool and used that to make my hd read-write but I only got that weird response. Now my hd won't mount, and I can't even access it. What just happened.

---

### Post by pappapump on 2007-06-04
Dont mess with it again till you can pull that hard drive out and put it in a windows 
machine and fix it or you'll lose everything.
Thats why I told you it's a bad idea to mess with it till you do a windows check.
Hopefully you didn't scramble things too badly.
I use a USB cable to attach a drive externally to my usb port and scandisk with windows.
It makes an internal drive an external one, cost me about $18.00 from meritline.

---

### Post by pacguy on 2007-06-04
Hmmm, new weirdness. When I pull up computer and access the drv4, the hd, I get a message saying I am not priviliged to mount the drive. But then I go to file systems/media/drv4 I can go right into it and add files. The /media/drv4 has only 82 gigs on it. When I go back to computer/drv4 and right click it to pull up properties, I get the normal options. Maybe if I edit the settings on mount properties, mount options, or file system fields under the drive or volume tab will have an effect on it.

---

### Post by pacguy on 2007-06-04
So then how do I fix my drive on a windows machine. That part confuses me.

---

### Post by pappapump on 2007-06-04
Once you're in windows just scandisk it and all will be well, if it don't hang.

---

### Post by pacguy on 2007-06-04
K. I'll give that a shot in the morning. Right now its 2 and I need to crash.

---

### Post by forger on 2007-06-04
> **pacguy said:**
> So then how do I fix my drive on a windows machine. That part confuses me.

try the ubcd for windows:
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)
[http://www.ubcd4win.com/howto.htm](http://www.ubcd4win.com/howto.htm)
[http://www.ubcd4win.com/downloads.htm](http://www.ubcd4win.com/downloads.htm)

With a windows cd, you'll be able to create a "live cd" environment, where you can see your hard drives, just like in winblows:
[http://www.ubcd4win.com/screen.htm](http://www.ubcd4win.com/screen.htm)

You have lots of hardware tools that come with ubcd4win, I hope you understand how to fix it now ;)

---

### Post by pappapump on 2007-06-04
I've heard good things about that program.
Hope it fixes him.

---

### Post by pacguy on 2007-06-05
Okay I tried hooking up my hd to another computer using windows, used the scandisk and properly shut it down. I hooked it back up to mine and I still can't get to it. The fdisk shows that my hd is there but I can't access it. Is there  a way for me to remount it so I can retrieve my files and then reformat the sucker.

Here's my fdisk. The drive I'm trying to get to is my hdd one.
> Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14311   114953076   83  Linux
/dev/hdc2           14312       14593     2265165    5  Extended
/dev/hdc5           14312       14593     2265133+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401    7  HPFS/NTFS

Any ideas.

---

### Post by Inxsible on 2007-06-05
could you post the output of ```
sudo fdisk -l
``` and ```
gksudo gedit /etc/fstab
```

I know you posted fdisk earlier, but you dont have an hda drive or a sda drive ..so i was wondering if you did it without sudo.

If all looks well in the fstab, then it might be a permissions issue which can be rectified by a sudo chown.

But one thing at a time

---

### Post by pacguy on 2007-06-05
Here's my fdisk.
> 
Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14311   114953076   83  Linux
/dev/hdc2           14312       14593     2265165    5  Extended
/dev/hdc5           14312       14593     2265133+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401    7  HPFS/NTFS

And here's my fstab
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/hdc1 :
UUID=14379de1-85d8-4d8d-80b0-0e1956a1d780	/	ext3	defaults,errors=remount-ro	0	1
#Entry for /dev/hdd1 :
UUID=6C1C20001C1FC44C	/media/DRV4_VOL1_	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/hdc5 :
UUID=15694024-3176-451a-9de4-1d666ee5b24c	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto	0	0
/dev/scd1	/media/cdrom1	udf,iso9660	user,noauto	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto	0	0
/dev/sdb1	/media/sdb1	ntfs-3g	defaults,locale=en_US.utf8	0	0

I managed to get my hdd mounted by mounting it as windows but I can only view the stuff. I can't copy it to my primary drive now. I just need to set it up so that I can copy my files from it then I'm going to reformat it.

---

