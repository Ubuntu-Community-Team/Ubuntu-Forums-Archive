---
title: "'Mount'ing stupidity on my part."
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by mreams13 on 2006-01-29
I've been reading the mount/fstab man pages for the last 3o minutes and I can't figure out how to do this.

I've got an Ext3 partition that I want to mount in my home directory. As soon as the partition is mounted, the mount point's permissions are changed to root and the user (Me) can't write to it.

Is there some way to change this? Have I lost my mind?

(Note to anyone: I don't want to create directories in this filesystem. I just want a ton of files smack dab in the middle.)

---

### Post by Sutekh on 2006-01-30
Assuming that you got it correctly mounted, try 'chmod' the mount point.

```
sudo chmod -R 777 /home/user/mount_point
```

This will allow read, write and execute permissions to the owner, group owner and everyone else (see table below)

_Octal number values_

Instead of characters, you can use the octal values to set permissions.

    * 0 = Deny all
    * 1 = Execute Only
    * 2 = Write Only
    * 3 = Execute and Write
    * 4 = Read Only
    * 5 = Read and Execute
    * 6 = Read and Write
    * 7 = Allow All

In the chmod command you use the combination of 3 numbers, the first number sets the permission for the owner of the file, the second for the group and the last for everybody else.

If this doesn't work, please post your fstab (I'm assuming that you are familiar with it now).

---

### Post by mreams13 on 2006-01-30
Yup, that works. I just don't really understand why. Does the filesystem remember that? Where is that info stored?

I only ask because the mount point is not changed if the filesystem is unmounted.

---

### Post by Sutekh on 2006-01-30
[QUOTE=mreams13]Yup, that works. I just don't really understand why. Does the filesystem remember that? Where is that info stored?

I only ask because the mount point is not changed if the filesystem is unmounted.[/QUOTE]

Well to my knoweledge its not the filesystem that remembers, but the folder that its mounted to, the mount point.

If the folder has full permissions then the filesystem mounted there should have those same permissions.

---

### Post by arsya on 2006-01-30
You can use the "uid", "gid", "umask" mount option in the fstab for the partition that you want to mount.

for example you can put something like below in your fstab

```

/dev/hda5 /home/user/<mount_point> ext3 users,rw,exec,auto,uid=<LogonName>,gid=<GroupName>

```


Hope it helps...

regards,
Arsya

---

### Post by mreams13 on 2006-02-02
[QUOTE=arsya]You can use the "uid", "gid", "umask" mount option in the fstab for the partition that you want to mount.

for example you can put something like below in your fstab

```

/dev/hda5 /home/user/<mount_point> ext3 users,rw,exec,auto,uid=<LogonName>,gid=<GroupName>

```
[/QUOTE]

No offense, arsya, but this does not work. (uid,gid and umask only work for some filesystems [I think NTFS is one], but does not work with ext2 or ext3).

Changing the permissions does, though. :KS

---

