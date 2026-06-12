---
title: "I would like to change my &quot;Mounting Rights&quot; for the CD &amp; Floppy"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-12
Hello everybody!

My experience with Ubuntu has been awesome!
Security & Safety are THE Best!!!
I am SO happy about it!!!

However, I have the following question:

I would like to change the "Mount" Rights for accessing the CD & Floppy.

I want the "Mount" Rights to be given only for the "**root**" user.

My "**/etc/fstab**" file looks like this:

root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
root@ubuntu:/#

What do I change at the above file to accomplish what I want?

**NOTE:**
At the same time, I can not Edit the "fstab" file with "gedit".

I have tried the following:

1. gedit /etc/fstab
2. gedit fstab            (from inside the "/etc" folder)
3. gedit /fstab

The Output was the following:
root@ubuntu:~# cd /
root@ubuntu:/# gedit /etc/fstab

(gedit:14208): Gtk-WARNING **: cannot open display:
root@ubuntu:/# gedit /fstab

(gedit:14213): Gtk-WARNING **: cannot open display:
root@ubuntu:/# cd /etc
root@ubuntu:/etc# gedit /fstab

(gedit:14218): Gtk-WARNING **: cannot open display:
root@ubuntu:/etc# gedit fstab

(gedit:14221): Gtk-WARNING **: cannot open display:
root@ubuntu:/etc#
root@ubuntu:/etc#

Thank you all for your time & effort,

Dimitris.

---

### Post by Sutekh on 2006-02-12
> **dvarsam]Hello everybody!

My experience with Ubuntu has been awesome!
Security & Safety are THE Best!!!
I am SO happy about it!!!

However, I have the following question:

I would like to change the "Mount" Rights for accessing the CD & Floppy.

I want the "Mount" Rights to be given only for the "root" user.

My "/etc/fstab" file looks like this:

root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 **user**,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,**user**,noauto  0       0
root@ubuntu:/#

What do I change at the above file to accomplish what I want?
[/QUOTE]
See where I've marked in bold said:**
> 
**NOTE:**
At the same time, I can not Edit the "fstab" file with "gedit".

I have tried the following:

1. gedit /etc/fstab
2. gedit fstab            (from inside the "/etc" folder)
3. gedit /fstab

The Output was the following:
root@ubuntu:~# cd /
root@ubuntu:/# gedit /etc/fstab

(gedit:14208): Gtk-WARNING **: cannot open display:
root@ubuntu:/# gedit /fstab

(gedit:14213): Gtk-WARNING **: cannot open display:
root@ubuntu:/# cd /etc
root@ubuntu:/etc# gedit /fstab

(gedit:14218): Gtk-WARNING **: cannot open display:
root@ubuntu:/etc# gedit fstab

(gedit:14221): Gtk-WARNING **: cannot open display:
root@ubuntu:/etc#
root@ubuntu:/etc#

Thank you all for your time & effort,

Dimitris.
It looks like you are at a command terminal (tty1) or something, rather than logged into a desktop environment (GNOME/KDE)

You can use **nano** to edit the fstab (first backup in case)
```
cp /etc/fstab /etc/fstab_backup
nano /etc/fstab
```

Then use nano to edit the lines mentioned.

---

### Post by yoyoned on 2006-02-12
if you don't want to use nano 
<code>
sudo gedit /etc/fstab</code>

---

