---
title: "installed NTFS configuration tool, still can't write to my NTFS disks"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by little brad on 2007-05-07
as the title states...

i'm running a dual boot setup with XP and fiesty. all of my music is on an external 500gb USB drive and i was using itunes to organize, play, burn, rip etc.. i can view and play the files in fiesty, but my concern is being able to add to my library later on.

i searched "NTFS" and found the NTFS config tool, successfully installed it.

go to the permissions for the drive itself, and it says 'owner unknown' and allows me the option to change the access rights, however when i do, it says "permissions could not be changed".

if i go into the drive and to the permissions of my "music" folder inside that drive, it says the owner is root and doesn't even allow me to change the option.

halp! :(

---

### Post by organica on 2007-05-07
> **little brad said:**
> as the title states...

i'm running a dual boot setup with XP and fiesty. all of my music is on an external 500gb USB drive and i was using itunes to organize, play, burn, rip etc.. i can view and play the files in fiesty, but my concern is being able to add to my library later on.

i searched "NTFS" and found the NTFS config tool, successfully installed it.

go to the permissions for the drive itself, and it says 'owner unknown' and allows me the option to change the access rights, however when i do, it says "permissions could not be changed".

if i go into the drive and to the permissions of my "music" folder inside that drive, it says the owner is root and doesn't even allow me to change the option.

halp! :(

Did you install the ntfs-3g module from synaptic?  This may be the missing link to getting NTFS read write to work correctly.

---

### Post by justleen on 2007-05-07
there should be a an application under Applications > System Tools > NTFS tool. runs this to enable write support.
(if its not inthe application > system tools menu, you will need the ntfs-3g-config package as well..)

---

### Post by little brad on 2007-05-07
> **justleen said:**
> there should be a an application under Applications > System Tools > NTFS tool. runs this to enable write support.
(if its not inthe application > system tools menu, you will need the ntfs-3g-config package as well..)

i ran the app, selected 'enable write support' for both internal and external devices and hit okay.

do i need to reboot?

---

### Post by little brad on 2007-05-07
> **organica said:**
> Did you install the ntfs-3g module from synaptic?  This may be the missing link to getting NTFS read write to work correctly.

i used this HOWTO

[http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS](http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS)

---

### Post by little brad on 2007-05-07
okay, rebooted and still nothing. now when i go to the permissions of the drive i don't have the option to change. says the owner is root. :(

---

### Post by Bryan Stark on 2007-06-30
Same problem: running 'ntfs-config' in the terminal rings up a dialogue box headed NTFS Configuration Tool.   I ticked both the box 'Enable write support for external device' and  'Enable write support for internal device' and checked the Advanced confiruration where all my ntfs partitions on two other Hard discs show that they are apparenlty writable.

My fstab file looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sdc1	/media/New_Volume	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
/dev/sdc2	/media/New_Volume_	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
/dev/sda3	/media/OS	ntfs-3g	defaults,umask=0,fmask=0,locale=en_GB.UTF-8	0	0
/dev/sda2	/media/RECOVERY	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
/dev/sdb5	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto	0	0

but, when I try to edit a file on one of my Windows Vista ntfs partitions using 'wine' and microsoft wrod it says the file is 'read only'.

Can this be changed to 'read' and 'write'?

---

### Post by SummerNight on 2007-06-30
I use the following to mount my NTFS external drive:

sudo mount -t ntfs-3g /dev/sda1 /media/usbdrive1

The NTFS-3g I downloaded and installed via Automatix. I placed the above in a file and just execute it when I want to mount the drive (which is not all of the time). Read and write works fine to it as any user on the system. If the volume is dirty then add -o force to the end of the command.

---

