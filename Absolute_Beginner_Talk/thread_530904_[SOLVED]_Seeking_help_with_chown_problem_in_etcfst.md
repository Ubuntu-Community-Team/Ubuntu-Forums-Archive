---
title: "[SOLVED] Seeking help with chown problem in /etc/fstab"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-08-21
I am stuck trying to change the ownership of /media/bigdrive from root to my login name, m9ke, so I can write to it without using sudo, and unmount the drive for a fsck.  This is a second drive I just added, which is currently empty.

To do that, I got some advice on this forum all of which worked great up to this point:

```
gksudo gedit /etc/fstab
```

The above got me into fstab just fine, where I added the following

```
sudo chown -R m9ke:m9ke /media/bigdrive
ls -la /media
```

Note that there is a return between "bigdrive" and "ls" above.

In the file browser, I see that root is the owner for both File System and bigdrive.

When I try to copy a file to this drive, I get "Error while copying to media/bigdrive.  You do not have permissions to write to this folder."

When I try to unmount bigdrive I get "Cannot unmount volume.  You are not privileged to unmount this volume.  Details [mntent]:  Line 14 in /etc/fstab is bad.  unmount: Only root can unmount /dev/sdb1 from /media/bigdrive."

Note that the code line above beginning with sudo chown is line 14 in /etc/fstab.

I am pretty sure that I copied this code in exactly as I was advised, but something is not working because ownership is not getting changed.

Can anyone correct my line 14 to enable me to change ownership? 

Thanks,
m9ke

---

### Post by lloyd_b on 2007-08-21
> **m9ke said:**
> I am stuck trying to change the ownership of /media/bigdrive from root to my login name, m9ke, so I can write to it without using sudo, and unmount the drive for a fsck.  This is a second drive I just added, which is currently empty.

To do that, I got some advice on this forum all of which worked great up to this point:

```
gksudo gedit /etc/fstab
```

The above got me into fstab just fine, where I added the following

```
sudo chown -R m9ke:m9ke /media/bigdrive
ls -la /media
```

Note that there is a return between "bigdrive" and "ls" above.

In the file browser, I see that root is the owner for both File System and bigdrive.

When I try to copy a file to this drive, I get "Error while copying to media/bigdrive.  You do not have permissions to write to this folder."

When I try to unmount bigdrive I get "Cannot unmount volume.  You are not privileged to unmount this volume.  Details [mntent]:  Line 14 in /etc/fstab is bad.  unmount: Only root can unmount /dev/sdb1 from /media/bigdrive."

Note that the code line above beginning with sudo chown is line 14 in /etc/fstab.

I am pretty sure that I copied this code in exactly as I was advised, but something is not working because ownership is not getting changed.

Can anyone correct my line 14 to enable me to change ownership? 

Thanks,
m9ke

Could you please post the contents of your "/etc/fstab" file?  For one thing, that "chmod" command does *not* belong in there.

What I suspect is that you need to create/modify the fstab entry for "/media/bigdrive", but without seeing what you've got now, it's difficult to tell you what you need to do.

Lloyd B.

---

### Post by eentonig on 2007-08-21
You can't chown in your fstab. 

/etc/fstab is only to mount drive at startup. Not changing ownership.

---

### Post by sunexplodes on 2007-08-21
Yeah, just enter that Chown command in the terminal, after a sudo. Should work fine.

---

### Post by m9ke on 2007-08-21
I should have mentioned in my first post I am running Fiesty.

Here is the contents of /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=546ac65c-081d-42f0-9970-3a771d313a46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1a5b433c-aeb6-4fa1-9fd7-ef7fc763ffa2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb /media/bigdrive ext3 defaults 0 0
/dev/sdb1   /media/bigdrive   ext3   defaults   0   1
sudo chown -R m9ke:m9ke /media/bigdrive
ls -la /media
```

Thanks,
m9ke

---

### Post by m9ke on 2007-08-21
Read the previous posts.  Took line 14 out of /etc/fstab

Ran that same string in terminal.  Got the following output:

```
m9ke@m9ke-desktop:~$ gksudo gedit /etc/fstab
(gedit:9058): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
m9ke@m9ke-desktop:~$ sudo chown -R m9ke:m9ke /media/bigdrive
m9ke@m9ke-desktop:~$ ls -la /media
total 24
drwxr-xr-x  6 root root 4096 2007-08-21 11:30 .
drwxr-xr-x 21 root root 4096 2007-05-30 17:49 ..
drwxr-xr-x  3 m9ke m9ke 4096 2007-08-18 04:21 bigdrive
lrwxrwxrwx  1 root root    6 2007-05-10 10:13 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-05-10 10:13 cdrom0
drwxr-xr-x  2 root root 4096 2007-05-10 10:13 cdrom1
lrwxrwxrwx  1 root root    7 2007-05-10 10:13 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-05-10 10:13 floppy0
-rw-r--r--  1 root root    0 2007-08-21 11:30 .hal-mtab
--wxr-x---  1 root root    0 2007-04-15 04:56 .hal-mtab-lock
m9ke@m9ke-desktop:~$ 
```

Thanks for answering my post, and I hope this helps.
m9ke

---

### Post by eentonig on 2007-08-21
remove these commands from fstab.

> 
sudo chown -R m9ke:m9ke /media/bigdrive
ls -la /media

And change 
> /dev/sdb1   /media/bigdrive   ext3   defaults   0   1

to

> /dev/sdb1   /media/bigdrive   ext3    rw,user,noauto   0   1

I think that should do the trick.

---

### Post by m9ke on 2007-08-21
eentonig, 

While you were posting I removed

```
sudo chown -R m9ke:m9ke /media/bigdrive
ls -la /media
```

I then verified that I could write a file out to the drive.

However I still can not unmount the drive, get 

> Cannot unmount volume. You are not privileged to unmount this volume. Details unmount: Only root can unmount /dev/sdb1 from /media/bigdrive.

Rebooted & tried unmount again, no joy.

Read your latest post.  Do you think that changing 

> /dev/sdb1 /media/bigdrive ext3 defaults 0 1
to


> /dev/sdb1 /media/bigdrive ext3 rw,user,noauto 0 1

Will allow me to unmount the drive?  If not do you know how I might address that?

Thanks very much for the help!
m9ke

---

