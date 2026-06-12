---
title: "windows partiton permissions"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-28
I have created a directory labeled windows in my /media/windows and editied my fstab.  It is a NTSF file system and I want read only. 

I tride to change permissions using sudo chmod -R 777 <mount point> it runs through my windows stuff and when its finished I still do not have permissions to view the contents of windows.

Any help would be great.

---

### Post by taurus on 2006-11-28
You cannot use chmod for ntfs or fat32.  It's not going to work.  If you want to write to ntfs, then you need to install ntfs-3g!  

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by gentlemanmasher on 2006-11-28
just want read only

---

### Post by taurus on 2006-11-28
What does your /etc/fstab look like then?  I assume that's how you mount your NTFS!

```
cat /etc/fstab
```

---

### Post by gentlemanmasher on 2006-11-28
caippers@caippers-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=5c474c3f-0ffb-4b09-aa1a-f1b310159251 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=1187a89e-b584-4b85-8772-de04a4b6d230 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



/dev/hdb1 /second_drive ext3 defaults 0 0  
/dev/hda1           /media/windows ntfs   defaults       0         0  
  

caippers@caippers-desktop:~$

---

### Post by taurus on 2006-11-28
Modify your /etc/fstab 

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and modify the entry for your ntfs to look like this now.

```
/dev/hda1  /media/windows  ntfs  defaults,umask=0222  0  0
```
Reboot and you now have read permission of your /media/windows...

p.s.  Your entry for /dev/hdb1 is a little odd.  The last value for it should be 1, not 0...

```
/dev/hdb1  /second_drive  ext3  defaults  0  1
```

---

### Post by gentlemanmasher on 2006-11-28
That worked thanks.

I have a couple questions if you have time.

1.  What is the difference between using gksudo gedit /etc/fstab and sudo nano /etc/fsab

2.  When adding a drive /dev/hda1  /media/windows  ntfs  defaults,umask=0222  0  0  How do I know what the umask is and you mentioned my last entry should be a 1 and not a zero.  How do you know what it should be and what made my entry incorrect.

sorry trying to learn as I go.

---

### Post by taurus on 2006-11-28
> **gentlemanmasher said:**
> That worked thanks.

Great.

> I have a couple questions if you have time.

1.  What is the difference between using gksudo gedit /etc/fstab and sudo nano /etc/fsab

2.  When adding a drive /dev/hda1  /media/windows  ntfs  defaults,umask=0222  0  0  How do I know what the umask is and you mentioned my last entry should be a 1 and not a zero.  How do you know what it should be and what made my entry incorrect.

sorry trying to learn as I go.
1.  Since gedit is a GUI text editor, you need to open it with gksudo.  On the other hand, nano (or vi) is just a standard text editor so you can run it with sudo.  In other words, sudo for terminal and gksudo for GUI.

2.  For vfat, you want to use umask=000 which means everybody can read or write to it.  And for ntfs, you want to use umask=0222 since you can only read from it.  Again, umask only applies for vfat and ntfs.  For ext3, you can set the permissions, read & write, with the chmod command.  And because of that, the last two numbers are either "0 1" or "0 2".

---

### Post by gentlemanmasher on 2006-11-28
Thanks now it makes sense.  I appreciate your help.

---

### Post by taurus on 2006-11-28
No problem and good luck.

---

