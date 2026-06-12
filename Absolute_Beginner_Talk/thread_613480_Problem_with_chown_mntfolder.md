---
title: "Problem with chown mnt/folder"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by desk2web on 2007-11-15
I've created some mount points within the mnt folder, and have successfully added them to fstab

However, Ive a problem in that I cannot save to the mounted drives - a check of the permissions on the folders showed the owner as root - so I tried to chmod the folder to allow me to have access:

root@webspace-linux:/mnt# sudo chown allan:users /mnt/web-spaced
chown: changing ownership of `/mnt/web-spaced': Operation not permitted

also tried...

allan@webspace-linux:~$ sudo chown allan:users /mnt/web-spaced
[sudo] password for allan:
chown: changing ownership of `/mnt/web-spaced': Operation not permitted
allan@webspace-linux:~$ 


What am I doing wrong?  I'm desperately trying to learn and as far as I can see what I've done should have worked?

Help!

---

### Post by bodhi.zazen on 2007-11-15
My guess is that the file system is either FAT or NTFS (windows).

With windows partitions you set ownership and permissions at the time of mounting.

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by desk2web on 2007-11-15
Hi, and thanks for the reply, the set up is as follows:

Internal hard drive - purely linux formated

Network drive accessed via //FND/sharename formated FAT32

I have been experiencing intermittent success, all shares were set up at the same time, I then set up the mnt/folder's, edited the FSTAB file and find that some of the shares are accessible some of the time but not all the time - very frustrating.

I havent even tried to put on the external USB drives yet !

---

