---
title: "Is there a higher authority than SU/root?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-06
While trying to save an Audacity file to an existing directory on a FAT32 partition, I've ran into a problem. The system (Edgy) throws up an error saying I don't have permission to save there. 

I looked at the permissions of the directory in question. Root is the owner, plugdev is the group. Both have full rights. I ran Nautilus as root (gksudo nautilus) and tried to change ownership. No go, a popup says I (as root) don't have permission to change the ownership. I tried from the terminal using chown. ```
sudo chown pk:pk /media/hda6/music
```

Denied again:
```
chown: changing ownership of `/media/hda6/music': Operation not permitted
```If root cannot change the ownership of this directory, who can?

---

### Post by taurus on 2007-02-07
You cannot use chmod or chown with ntfs or vfat even as root.  You can, however, set the ownership of vfat through /etc/fstab.

Why not so something like this from a terminal.

```
sudo umount /dev/hda6
sudo mount -t vfat /dev/hda6 /media/hda6 -o iocharset=utf8,umask=000
```
Now, you can write to /media/hda6.

---

### Post by 23meg on 2007-02-07
The problem is that the FAT32 filesystem doesn't recognize per file permissions since it's not a Linux filesystem. You'll have to mount the entire filesystem as user readable.

---

### Post by bodhi.zazen on 2007-02-07
Is there a higher authority than SU/root?

Of course, the Ubuntu forums :p

At any rate, the problem is that you are working with a FAT file system which knows nothing of permissions.

You can change the owner/group at mount or in fstab.

Unmount the partition, re mount it with these options:

```
sudo mount /dev/hda6 /media/hda6 -o gid=100,uid=1000,umask=000
```

Add those options to fstab:

> /dev/hda6 /media/hda6 auto users,uid=100,gid=1000,umask=000 0 0

If you are paranoid you can use a different group or umask value.

See here for further info:

[http://www.ubuntuforums.org/showthread.php?t=283131](http://www.ubuntuforums.org/showthread.php?t=283131)

---

### Post by Patrick K on 2007-02-07
Thanks, for the replies. I looked at some man pages but don't really understand all they say. However, the code worked and I can save the file to the directory I want. Thanks again.

---

### Post by konungursvia on 2007-02-22
> **23meg said:**
> The problem is that the FAT32 filesystem doesn't recognize per file permissions since it's not a Linux filesystem. You'll have to mount the entire filesystem as user readable.

Wow non linux filesystems suck!:) :guitar: :lolflag:

---

### Post by Bachstelze on 2007-02-22
In a nutshell : if it can't be done, even root can't do it ;)

---

