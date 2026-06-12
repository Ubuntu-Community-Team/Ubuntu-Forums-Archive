---
title: "backup using rsync to usb disk (vfat) problem"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by bouwsupport on 2005-11-07
I am struggling for a while now to make backups using rsync.

The problem is that i want to backup a folder which is shared as 'projectfolder' and holds all my projects.

The idea was to make icremental backups to an external USB 2.0 disk which is formatted as vfat32 partition. Using rsync and some scripts on the forum I came up with:

```
/usr/bin/rsync -avz --delete --link-dest=/media/usbdisk/week1/monday /home/bbs/Server/ /media/usbdisk/week1/tuesday/
```

It works like this: on monday's there will be a full backup of all the files on the home/bbs/Server/ folder to the external disk, every day of the week i'm using the code above to create an incremental backup of my files using hard links.

The problem is, it is totally inconsistent, one day it backs up all my files, not incremental, and on another day is skips almost 300 projects!

Is it because the vfat partition? Is it the code? Please help!

---

### Post by ras on 2006-04-03
I am dual booting and having the same problem.  I want to keep identical directories on both my /home ext3 partition and a mounted vfat (FAT32) partition.  The mounted vfat partition is mounted as '/shared' and the source dir is /home/*/agrenfiles/.

```
# Rsync agren files with home directory
# Source dir: /home/austin/mydocs/agrenfiles/
# Target dir: /shared/
# code:
rsync -av --exclude-from=/home/austin/.rsync/exclude-agren --stats /home/austin/mydocs/agrenfiles/ /shared/
```

When I run the script, I get a lot of errors.  For example:
```
rsync: mkstemp "/shared/misc/.networkcard2.txt.95xtXW" failed: Operation not permitted (1)
rsync: mkstemp "/shared/misc/.pppoeconf.txt.cvyr3z" failed: Operation not permitted (1)
rsync: mkstemp "/shared/misc/.serverIP.txt.jY1Ibd" failed: Operation not permitted (1)
rsync: failed to set times on "/shared/agren/400-writing/450-tgm": Operation not permitted (1)
rsync: failed to set times on "/shared/agren/500-education": Operation not permitted (1)
rsync: failed to set times on "/shared/agren/600-management": Operation not permitted (1)
```

I keep creating test files to see if they actually show up on the vfat partition, and they never do.

Any suggestions?

ras

---

### Post by bscbrit on 2006-04-03
First of all, what is 'mkstemp' - do you mean 'mktemp'?

Are you sure that you have r/w permissions for your vfat partition?

---

### Post by ras on 2006-04-03
bscbrit, I am not sure what 'mkstemp' means, but it was directly copied from the terminal output from the command shown in my first post.  Here is my /etc/fstab:
```

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda6       /shared         vfat    umask=000       0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

As you can see, I used 'umask=000 0 0' for the vfat partition (hda6).  I dont know what this means or does because I am a newbie, but I got it directly from the official ubuntu starter guide.  So to answer your question, no I do not know if I have read/write permissions, but perhaps you can tell. Thanks for your help.

ras

---

### Post by bscbrit on 2006-04-03
What I _think_ is causing the problem is using rsync to copy between the ext2/3 partition and the vfat partition.  The reason is that rsync is trying to access information regarding each file stored on the vfat partition (e.g. creation time, user, permissions etc) but this information is not stored in a vfat partition.

Try simply copying one file from the ext2/3 to vfat partitions using 'cp'.  If that works, then you have all the access permissions that you require, and the problem is with trying to use rsync.  If that doesn't work, then you still do not have the appropriate access permissions for the vfat partition.  You can also check by using 'ls -l /shared' and see what the results are.

---

### Post by ras on 2006-04-03
Yeah, I can copy files onto the vfat partition with no problems, so I think you're right.  In fact, the only time I encounter problems is when I use rsync.  The output from ls -l /shared:

austin@austinlt:/$ ls -l /shared
total 40
drwxrwxrwx  12 root root 8192 2006-03-31 14:19 agren
drwxrwxrwx   2 root root 8192 2006-03-29 08:34 backup
drwxrwxrwx   3 root root 8192 2006-03-31 14:43 misc
drwxrwxrwx   3 root root 8192 2006-03-29 07:32 Recycled
drwxrwxrwx   3 root root 8192 2006-03-29 07:10 System Volume Information

This output indicates that maybe I can't rsync onto it because I am not the owner.  But how do I fix it so that I am?  I have tried 'chown' and 'chmod' to no avail.  Perhaps it is how I am mounting it.  Maybe I should mount it as another number than umask=000.  I don't know.

I modified the script to use 'sudo', and it proceeded to add all the files to the vfat partition that I had been having trouble with.  Now the trouble is I can't open these files without root permission.  I don't know what to do.

ras

---

### Post by senorJ on 2006-08-22
I'm Having Exactly the same problem as ras.

Did you manage to sort this ?

Jay

---

### Post by senorJ on 2006-08-23
I've sorted it now thanks to this post - [http://ubuntuforums.org/showthread.php?t=187894&highlight=Backup+multimedia+rsync](http://ubuntuforums.org/showthread.php?t=187894&highlight=Backup+multimedia+rsync)

---

### Post by paulojjs on 2006-12-20
> **ras said:**
> This output indicates that maybe I can't rsync onto it because I am not the owner.  But how do I fix it so that I am?  I have tried 'chown' and 'chmod' to no avail.  Perhaps it is how I am mounting it.  Maybe I should mount it as another number than umask=000.  I don't know.

Use the option uid=*your_username* when mounting the partition, that should solve your problem with rsync.

---

### Post by paulojjs on 2006-12-20
Btw the problem is that rsync uses mkstemp(3) to create temporary files. Since this creates temporary files with 0600 permissions and vfat fs uses the same uid to all files the file creation fails.

Forcing your uid on the filesystem will allow the temporary files creation.

---

### Post by QwUo173Hy on 2007-01-05
I was just having a similar problem, where I was constantly getting the error that it "failed to set times". As previously stated, vfat doesn't store this info, so I used the option --size-only which ignores the timestamp.

---

