---
title: "writing to hfs+ partition // help!"
date: 2007-07-06
forum: Apple PPC Users
---

### Post by jaskah on 2007-07-06
hello
i am trying to write files to an hfs+ partition (unjournaled) on my titanium g4 powerbook and get the following message:
¨Error while copying to ¨media/files¨
You do not have permissions to write to this folder.¨
how can i change this?
thanks!
jason

---

### Post by joninkrakow on 2007-07-06
I believe you have to turn of journaling via the Disk Utility in OS X for this to work. I haven't gotten my external to show up at all, so I haven't been able to test this on my own setup.

-Jon

---

### Post by jaskah on 2007-07-06
hi jon
thanks for your reply. as i mentioned here, journalling is off. but i still can't access this partition. 
i have the permissions written for read+write as "owner," "group,' and "others."
my external shows up, no problem (and i can read+write to it), and i can also access the partition where my os x system is.
anybody else have an idea what the problem could be?
jason

---

### Post by pxwpxw on 2007-07-06
In addition to all the other requirements , in ubuntu  if the partition is included in /etc/fstab, the directory under which it is mounted needs permissions to allow writing.  That is not done during the installation, the permissions were read only.  It happens  during the partitioning part of the install if you allow some hfs partitions to be mounted at startup. However there might be more to the story.

---

### Post by jaskah on 2007-07-06
thanks for your help.
this is exactly my problem...i only have read-only privileges for this hfs+ partition.
how can i change the permissions of this partition to read-write? i've tried this in os x but it didn't make a difference once i got back to linux. i also tried this in the fstab but this didn't make a difference either.
jason

---

### Post by pxwpxw on 2007-07-06
This has been edited from my xubuntu system to demonstrate, do not use as a model.

In ubuntu linux:

The Macos extended but not journalled partition /dev/sdb9 is mounted on directory /media/mac2
```

max@bigmac:~$ cat /etc/fstab
# /etc/fstab: static file system information.
## other entries not shown ----
# /dev/sdb9
UUID=566bdd98-2494-4c1f-ab0b-5c2e9107b517 /media/mac2	  hfsplus    defaults   0  0
#

max@bigmac:~$ cd /media/
The default permissions for /media/mac2 are read only for group and others

max@bigmac:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2007-05-19 01:48 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-05-19 01:48 cdrom0
drwxr-xr-x 4 root root 4096 2007-07-06 22:21 mac2

Change to readwrite for group and others 

max@bigmac:/media$ sudo chmod go+w mac2/

admax@bigmac:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2007-05-19 01:48 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-05-19 01:48 cdrom0
drwxrwxrwx 4 root root 4096 2007-07-06 22:21 mac2

```

This is unsecure, giving write access to anyone, to see if it gives the access you need. Wrie access should be restricted to a local user or group.

If you have tried this and it doesn' work, then I am out of ideas.

========================

---

### Post by jaskah on 2007-07-07
thanks for your help!

one other question: how did you get this id number for your mac partition:
UUID=566bdd98-2494-4c1f-ab0b-5c2e9107b517 

in the end, i now only have two partitions on my computer: one for ubuntu and one for osx. after changing all my permissions in ubuntu to correspond to mac osx it seems i can freely read and write all files on the mac os x partition.
i could never get this far with an additional partition.
jason

---

### Post by pxwpxw on 2007-07-07
The UUID is allocated by the installer, but it was not relevant, it was only the permissions that were  significant in that example.
Is you problem fixed now?

---

