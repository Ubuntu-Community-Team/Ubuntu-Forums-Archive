---
title: "Additional hard disks"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Akt on 2007-05-17
I'm new to Linux so be easy.  I have Ubuntu 6.06LT, I installed it on the dev/hda1 partition.  I have a second drive that is NTFS (dev/hdb1) with all my data on it, I edited my fstab file and now I can read the data thanks to these forums (but still cannot write to that drive).  I installed a new drive (dev/hdd) and created an Ext3 parition and I can read the drive, but I cannot write to it.  WTF?!  help me please.  My goal is to transfer the data on hdb1 to hdd so I can manipulate it as I see fit, but I can't write to either of these drives.  Here's my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /home/Data ntfs umask=0000 0 0

Please, if you can help remember I'm a NEWB!  Yay, no more M$!  Linux rocks, except for this hard drive crap, :P

---

### Post by gradedcheese on 2007-05-17
The mount options should be set to "user,rw" for "users may mount, read, write" in this case.  So:

/dev/hdb1 /home/Data ntfs umask=0000 0 0

becomes...

/dev/hdb1 /home/Data ntfs user,rw  0 0

You can also adjust the umask instead.

---

### Post by Akt on 2007-05-17
Cool, thanks for the quick response.  That leads me to two other questions...

1. How would I edit the umask instead?

and

2. The hdd device isn't in the fstab file but it is mounted, I just can't write to it.  It is ext3 partitioned after I installed Ubuntu then added the blank new drive.  So, would I need to add a line the fstab for it as well?

Thanks!!!

---

### Post by gradedcheese on 2007-05-17
The umask sets user permissions as an octal number.  The 'rw' accomplishes the same in text form.  When you "ls -l" in a directory and see things like "drwxr-xr-x", you're seeing the text representation of the mask.  

You can add a line for each drive to /etc/fstab to have them mounted automatically.  The stuff you put there is based on what you typed to manually mount the drive.  You need to edit the file with sudo, ex "sudo gedit /etc/fstab"

Each line is divided into device, mount point, type, options, dump, and pass.  The device is /dev/hda1 and the like.  The mount point is where to mount (/mnt/disk1 for example), the type is the file system type (ex: ntfs or ext3), options set the mount options (ex: user,rw).  So you can add:

/dev/hdd0 /home/OtherDisk ext3 user,rw 0 0

For example (assuming you want partition 0 on /dev/hdd).  Make a directory for the mount point like you did for the other disk.  Usually you put these in /mnt, rather than /home

You can also read more about fstab if you are curious, "man fstab" (scroll down and then q to exit).  The last two options (dump and pass) specify whether the drive will be checked on bootup.

---

### Post by Akt on 2007-05-17
Great information, again thanks for replying so quickly.

I applied the changes you suggested and now my NTFS drive is unavailable again, no access at all.

Here's my fstab again for analyzation:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdb1 /home/Data ntfs umask=0000 0 0
/dev/hdb1 /home/Data ntfs user,rw 0 0

---

### Post by gradedcheese on 2007-05-17
hmm, what if you do

```

sudo mount -a
ls /home/Data

```

---

### Post by Akt on 2007-05-17
I get 'permission denied' with those commands.

:(

---

### Post by gradedcheese on 2007-05-17
oops, it looks like for Windows file systems you need to use umask after all (sorry, I didn't know that).  Try changing the mask, so basically change options to say something like "umask=666".  Another issue might be that the NTFS driver with your system could only support reading.  There's a newer driver that can write safely as well, but I am not sure if it came on 6.0.6.  NTFS support is reverse engineered so it took a long time to have it work :(  'love this microsoft standards...

---

### Post by Akt on 2007-05-17
Ok, changing to 'umask=666' removed my access to the drive altogether again...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /home/Data ntfs umask=0000 0 0
/dev/hdd1 /home/Drive2 ext3 user,rw 0 0

...is what I'm running right now and the hdd1 (extended 3) still won't let me write to it.  At least I can see the data on hdb1 (NTFS), if I can just get write access to hdd1 I could be in business.

I really appreciate all your help.

---

### Post by Akt on 2007-05-17
Ok, I did a little more searching and found how to make the hdd1 writable.

akt@akt-desktop:~$ cd /home
akt@akt-desktop:/home$ cd Drive2
akt@akt-desktop:/home/Drive2$ sudo chmod 777 *

After a minute or so, everything worked out grand!

Thanks!

I'm now a Linux man for life!  Eff M$!  hehe.

---

