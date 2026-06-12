---
title: "NTFS default mount"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by PPisHere on 2006-01-11
Hi there,

I think I made proper decision and changed from Fedora to Ubuntu-Breezy :KS 
But I have tiny question about default Windows partition mounts (I mean default that installer does).

My fstab uses 'default' options for /dev/hda1 (win partition), and as far I understood it means 'nouser' option, so only root can mount/use win partitions.
Why is that? 'user' option might be better.

OK, this is no problem since ubuntu guide has good solution: [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

But is there any explanation about *nouser *over *user*

---

### Post by Sef on 2006-01-11
Nouser is the default, so no one can go in and read, or write, or both unless they are allowed to.  This is done for networks, where only certain people would be allowed to access the data.  On a home computer, where only you are accessing the files, user would be just fine.

---

### Post by M3lted on 2006-01-11
i did follow the link and my windows partition are mounted , but do they get mounted on boot now to ?
if not what do i need to change then :)?

thx

---

### Post by epostma on 2006-01-11
M3lted: No, what this does is just mount (or unmount) the partition once. To get it mounted automatically at boot time, you need to edit the file /etc/fstab. This file can only be edited as root user, so you could type
```
sudo gedit /etc/fstab
```
or
```
EDITOR=gedit sudoedit /etc/fstab
```
to edit it with the gedit editor.

You need to add a line to this file like the lines that are already there: it should first have the name of the partition that contains the filesystem, then where to mount it, then the filesystem type, then some options, and then probably two zeroes. Now if you typed 
```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```
in order to mount the filesystem as in the ubuntuguide URL, then you would add the line
```
/dev/hda1   /media/windows    ntfs   nls=utf8,umask=0222,auto   0   0
```
to /etc/fstab. Adding the word 'auto' makes it automatically mount the filesystem at boot time and unmount it when you shut down.

If you want to be able to mount or unmount it in between as a regular user, that is, without having to type sudo, you could add the option user. That would make it
```
/dev/hda1   /media/windows    ntfs   nls=utf8,umask=0222,auto,user   0   0
```
Take note that there are no spaces in between the options, only commas!

HTH,

---

### Post by frodon on 2006-01-11
A good link to get informations about fstab options : [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by M3lted on 2006-01-11
well i edit the fstab file and added this 
```

/dev/hda1   /media/windows    ntfs   nls=utf8,umask=0222,auto   0   0
/dev/hdb1   /media/windows    ntfs   nls=utf8,umask=0222,auto   0   0

```
and it works like a charm thx for the help guys :)
it even add's 2 nice icons to my desktop :D

---

### Post by PPisHere on 2006-01-12
[QUOTE=M3lted]well i edit the fstab file and added this 
```

/dev/hda1   /media/windows    ntfs   nls=utf8,umask=0222,auto   0   0
/dev/hdb1   /media/windows    ntfs   nls=utf8,umask=0222,auto   0   0

```
and it works like a charm thx for the help guys :)
it even add's 2 nice icons to my desktop :D[/QUOTE]

If there are two /media/windows, how does Ununtu/Linux makes difference between them. If you take *ls* from /media dir what do you get? I assume that there cannot be two dirs with same name.

---

### Post by daschl on 2006-01-12
[QUOTE=PPisHere]If there are two /media/windows, how does Ununtu/Linux makes difference between them. If you take *ls* from /media dir what do you get? I assume that there cannot be two dirs with same name.[/QUOTE]

yeh thats correct.

create as root a different directory and edit the fstab file so that it points to the new directory

(remeber that a directory is also a link to somwhere on your hard drive ;)) it cant point on two different places

[http://lists.debian.org/debian-user/2001/11/msg00706.html](http://lists.debian.org/debian-user/2001/11/msg00706.html)

---

