---
title: "[SOLVED] umask question"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by kaiju on 2008-02-01
i'm trying to set some file permissions to read/write for user, read-only for group and none for others. the best guess i got this far is umask 640, but this way directories are locked for the user, too.
how can i keep the files' permisiions, but also make the directories executable?

---

### Post by bodhi.zazen on 2008-02-01
Depends on the file system, FAT/NTFS vs. linux native (ext2/3, reiserfs)

FAT/NTFS, permissions for the ENTIRE PARTITION are set at teh time of mount with the options

uid=xxx,gid=yyy,umask=zzz

For linux native use chwon and chmod.

---

### Post by kaiju on 2008-02-01
thanks. i take this to mean that i can't set permissions for a reiserfs partition at mount time.
and i still haven't figured out the right chmod parameter to make directories executable (=readable).

---

### Post by bodhi.zazen on 2008-02-01
> **kaiju said:**
> thanks. i take this to mean that i can't set permissions for a reiserfs partition at mount time.
and i still haven't figured out the right chmod parameter to make directories executable (=readable).

for resierfs, you set the ownership and permissions after you mount (this is a one time change and will survive reboot and re mount).

In the following example, change "/mount/point" to the actual mount point on your file system (/media/???)

First, mount the partition.

sudo chown user.group /mount/point

change user to the user you want to own the mount point, and gruop to the group ownership. If you do not know what to use, you can :

```
sudo chown root.users /mount/point
```

Then set permissions :

```
sudo chmod 770 /mount/point
```

And on for sub directories 
sudo chown user.group /mount/point/directory
sudo chmod 770 /mount/point/directory

And files
sudo chown user.group /mount/point/directory/file
sudo chmod 770 /mount/point/directory/file

---

### Post by scorp123 on 2008-02-01
> **kaiju said:**
>  i'm trying to set some file permissions to read/write for user, read-only for group and none for others. the best guess i got this far is umask 640 ... Nope. You are counting wrong.

**chmod 755 == umask 022**

You still have those bits, where read+write+execute gives a value of 7 ... but in "umask" you count from the opposite end.

See my example above ... if you add the values of the "chmod" command and those of the "umask" command you always get 7 .... it's just they are counting from opposite ends. So where you'd use a value of "5" to grand read+execute permissions via "chmod" you'd use a value of 2 for "umask" to do the same (7 - 5 = 2).

This explanation is nowhere 'complete' in any way but I think you understand what I mean here.

---

### Post by kaiju on 2008-02-02
got it guys. thank you both :)

---

