---
title: "second hard disc"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-08-28
I am using ubuntu edgy 6.10.
I installed an 80gb hard disc, and made a partition in it of size nearly 20gb.

I find that partition as hdc1 from device manager.

So, I made a new folder in /media and named it hdc1, so that the folder becomes /media/hdc1. Very good.

But as soon as after mounting the device I reloaded the window, a cross mark appeared on the hdc1 folder!!
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=41852&stc=1&d=1188274471[/IMG]

As is expected, when I double click the hdc1 folder, it says
```
**The folder contents could not be displayed.**
You do not have the permissions necessary 
to view the contents of "hdc1".

```

Well what else could I do than to type in terminal
```

cd /media
sudo nautilus hdc1

```

However, the folder opens, but I can not `write', but can only read.

I did
```
cd /media
sudo su
chmod 777 hdc1

```
and moreover,
```
sudo su
cd /media/hdc1
chmod 777 *

```

Nothing did they do for me. Could you please help me?

---

### Post by bodhi.zazen on 2007-08-28
sudo chmod 777 /media/hdc1

---

### Post by sauravbhaumik on 2007-08-28
> **bodhi.zazen said:**
> sudo chmod 777 /media/hdc1


I did. It doesn't help. Please give other idea.

By the way, it is an ntfs partition, I forgot to say.

---

### Post by bodhi.zazen on 2007-08-28
Well, I would steer you away from ntfs

If you want to mount your ntfs rw you need to user ntfs-3g

ntfs-config is s gui front end : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

But I would advise a FAT partition if you want to share with windows, otherwise go with ext3 > ntfs

FYI you can mount an ext3 partition on windows : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by finer recliner on 2007-08-28
NTFS drives are only readable from ubuntu. you need to install ntfs-3g to be able to write to an NTFS partition.

---

### Post by alienexplorers on 2007-08-28
try > chown username:username /media/hdc1

---

### Post by bodhi.zazen on 2007-08-28
> **alienexplorers said:**
> try> chown username:username /media/hdc1

LOL :lolflag:

FYI, as you can see from this thread, that will not work. fat/ntfs partitions are handled differently from linux native partitions (ext2/3,reiserfs,etc).

With FAT/NTFS, ownership is set at the time of mount and chown (after mounting) will not work.

either mount bla bla -o uid=xxx,gid=yyy,umask=zzz

or in fstab

bla bla bla uid=xxx,gid=yyy,umask=zzz

see man mount or any guide on fstab for details.

In addition, as has been mentioned, one needs ntfs-3g for write access to ntfs partitions.

---

### Post by sauravbhaumik on 2007-08-28
> **bodhi.zazen said:**
> Well, I would steer you away from ntfs

If you want to mount your ntfs rw you need to user ntfs-3g

ntfs-config is s gui front end : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

But I would advise a FAT partition if you want to share with windows, otherwise go with ext3 > ntfs

FYI you can mount an ext3 partition on windows : [http://www.fs-driver.org/](http://www.fs-driver.org/)

I installed ntfs-config; and fired up
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=41859&stc=1&d=1188279388[/IMG]

I okayed it. But no change was there!!!!:(

Please suggest other applications.

---

### Post by bodhi.zazen on 2007-08-28
Nope, that is pretty much your option ...

I would :

1. Unmount and re-mount the device.

2. Reboot (ouch, I hate to reboot).

3. If that fails, add an entry in fstab and remount.

```
/dev/hdc1   /media/hdc1   ntfs-3g   user,uid=1000,gid=100,umask=007 0 2
```

To edit fstab, in a terminal :

```
gksu gedit /etc/fstab
```

---

### Post by sauravbhaumik on 2007-08-29
> **bodhi.zazen said:**
> Nope, that is pretty much your option ...

I would :

1. Unmount and re-mount the device.

2. Reboot (ouch, I hate to reboot).

3. If that fails, add an entry in fstab and remount.

```
/dev/hdc1   /media/hdc1   ntfs-3g   user,uid=1000,gid=100,umask=007 0 2
```

To edit fstab, in a terminal :

```
gksu gedit /etc/fstab
```

Hmm ..
I think it works; but you see, I have a vfat partition, in hda (it is hda6).
I added it to be automounted in fstab; but I can only read from it, not write.
Please explain the theory of mounting - I do not understand how it is. I really need to learn some theory.

Thanks

---

### Post by bodhi.zazen on 2007-08-30
vfat is different from ntfs

change the entry "nfts-3g" to either auto or vfat.

You set ownership in the options column of fstab or with the -o flag on mount

uid=xxx
gid=yyy
umask=zzz

umask sets permissions.

See these links :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)
[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)
[indent]scroll down to the umask section near the end[/indent]
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

If that last link does not cure your insomnia, nothing will :twisted:
Scroll down to the information on vfat and ntfs partitions ...

---

