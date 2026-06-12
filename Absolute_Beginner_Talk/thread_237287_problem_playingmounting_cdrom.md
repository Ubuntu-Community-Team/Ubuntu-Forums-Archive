---
title: "problem playing/mounting cdrom"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by qsc on 2006-08-15
I have been searching for a while, but did not find a solution. 
I will now describe the problem and terminal output step by step.

My laptop is Toshiba Satellite A105-S4211; it is supposed to have CD RW and DVD RW. But abosultely it has a CD ROM. I am runing Ubuntu 6.06.

1. I put in a audio cd, nothing happened. The cdrom did runs, but the audio was not playing. (Different from the description in Ubuntu Desktop Guide)

2. I go to places-->computer-->CD ROM1, double click CD ROM1.
Error output:Unable to mount the selected volume.
Reason: mount: special device /dev/scd0 does not exist

3. I tried to mount the cdrom manually.
code: sudo mkdir /mnt/cd1
      sudo mount -t iso9660 /dev/scd0 /mnt/cd1
error output: mount: special device /dev/scd0 does not exist

Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



I would guess that the optical device is not properly detected during the installation, but having no idea how this happens, and how to fix it. Any hint will be appreciately.

QS

---

### Post by qsc on 2006-08-16
The default kernel is i386. After initial installation I upgrade the kernel to i686-smp. Should this cause the problem? I know some user-installed driver depends on the kernel source, but not sure about this.

---

### Post by kebes on 2006-08-16
First off, maybe it's just that the name of the cd-rom device changed during the kernel upgrade? Check your devices:

```

ls /dev/scd*
ls /dev/cd*

```

On my system, for instance, the CD/DVD-burner mounts as /dev/cdrom and /dev/cdrw.

It might be as simple as updating your fstab to reflect the new device names.

---

### Post by chalex on 2006-08-16
What if you go to System -> Administration -> Disks?  Is the CDROM listed there?  Change the device name in /etc/fstab to match it.

---

### Post by qsc on 2006-08-16
Thank you all for the replies and hints. 
All of a sudden, this morning I found the problem fix itself. The audio cd now plays automatically. CDROM now is listed in the disk manager. What's more, CD R/W and DVD R/W all seem to be supported. The only excuse I can find for this is after several starting up of the system, the device is recognized  now.

---

