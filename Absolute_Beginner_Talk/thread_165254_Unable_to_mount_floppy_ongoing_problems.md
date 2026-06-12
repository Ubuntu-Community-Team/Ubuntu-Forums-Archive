---
title: "Unable to mount floppy ongoing problems"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by shanelayden on 2006-04-24
Howzit Ubuntu forums folk...

I am relatively new to the Ubuntu world and have **been trying rather unsuccessfully to get my floppy drive to mount and unmount correctly**! I have tried various methods that I found in various threads, but the problems continue. I am running Ubuntu Breezy 5.10. At first the floppy drives seemed to be mounting properly, but now they are not... It is really frustrating because I am in charge of a computer room at an institution where most people use floppy disks and I have installed Ubuntu on 9 of our PCs, unaware that this problem would persist in such a manner...

**I just need a straight forward simple way of sorting this out (how come the updates are unable to do this?), help...** I keep having to load the files onto my USB Memory Stick and then copying them to floppy disk on a Windows XP PC!

Other than this, and the Macromedia Flash Plug in mission which I eventually accomplished, **Ubuntu rocks!!!**

Shane (surrounded by unhappy floppy disk users)

---

### Post by steve.horsley on 2006-04-24
I haven't tried to use a floppy on Breezy, but I discovered I need to issue this command on Dapper before I can see floppies at all:
**sudo modprobe floppy**
If this fixes your problem, you can make it a permanent configuration by adding floppy to the list of required modules in /etc/modules.

After that, try this command to mount a floppy:
sudo mkdir /mnt/floppy
sudo mount -t vfat /dev/fd0 /mnt/floppy

another alternative to try is:
pmount /dev/fd0

See how you get on with these to start with

---

### Post by gr0kzer0 on 2006-04-24
I've also experienced problems with my floppy drive. Even though, so far as I can tell, the entries in /etc/fstab are correct, the drive won't automount. However, I _can_ manually mount and unmount the drive, with the commands sudo mount /dev/fd0 and sudo umount /dev/fd0. (I think the sudo is necessary) Someone on this site told me there was a bug in Breezy causing this, and there's a fix for the bug available. Unfortunately I lost the link for the bug fix and so never got round to fixing it. However, mounting and unmounting the drive manually isn't that big a deal, so I'm not really bothered. If you want it, a search for my threads will find the link for you.

---

### Post by dchey on 2006-12-02
Here is my /etc/fstab file. I added the line in bold and my floppy works great.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/fd0 /media/fd0 auto rw,user,noauto 0 0**

---

