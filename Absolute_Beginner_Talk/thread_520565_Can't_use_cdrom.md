---
title: "Can't use cdrom"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-08-08
Hi i just newly installed ubuntu Edgy on my notebook and I can't use the cdrom except to play music. When I want to open a data cd burnt on my primary box ....well the drive doesn't open unless i stick a pin in the front of the drive. I was able to see one data cd in the drive though. I did "sudo mount /dev/cdrom/cdrom" after googling to find out what to do but then i counldn't or didn't know how to unmount. I think I need to set up permissions to use the cdrom? I have had ubuntu on this notebook before but have forgotten how to do some things. Do I need to reverse what I did and then give permission for me as the User to access the cdrom?

---

### Post by overdrank on 2007-08-08
> **rapattack1 said:**
> Hi i just newly installed ubuntu Edgy on my notebook and I can't use the cdrom except to play music. When I want to open a data cd burnt on my primary box ....well the drive doesn't open unless i stick a pin in the front of the drive. I was able to see one data cd in the drive though. I did "sudo mount /dev/cdrom/cdrom" after googling to find out what to do but then i counldn't or didn't know how to unmount. I think I need to set up permissions to use the cdrom? I have had ubuntu on this notebook before but have forgotten how to do some things. Do I need to reverse what I did and then give permission for me as the User to access the cdrom?

Hi to unmount you should be able to right click on it from place, home and select unmount. THe same would apply if seen from the desktop. :)

---

### Post by steve.horsley on 2007-08-08
If you mounted ot with 
**sudo mount -t iso9660 /dev/cdrom** 
you will need ot unmount it with 
**sudo umount/dev/cdrom**
and notice the missing "n" in umount.
**sudo eject**
might work too.

You will not be allowed to unmount it if there is a command prompt or a file browser open on the drive, so you may need to close your file browser and cd home first.

Normally, putting a CD in makes an icon appear on the desktop, in which case you can unmount it by right-clicking the icon and choosing eject.

---

### Post by rapattack1 on 2007-08-09
There is no icon on the desktop or anything that I can click to unmount at all.

I didn't mount using that command steve. Can I use it now? Maybe I will try anyway and see.
I got this from the first command:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


and "sudo eject" worked!

Havent got a cd with me to test the drive as i am away from home.


Well the latest is....a friend gave me a command that mounted the drive but i don't remember it and now the drive doesn't mount.

---

