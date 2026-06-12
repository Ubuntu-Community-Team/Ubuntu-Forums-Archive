---
title: "mount NTFS partition- asks for password every time"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by sc30317 on 2007-12-07
Hello all,

I have a minor problem.  

on my hard drive, I have a Vista partition, a Gutsy partition, and an NTFS data partition.

When I open ubuntu, my Vista partition is read/write perfectly from turning on the laptop
When I go to open my data partition; however, I have to enter a password before I can read/write

This is anoying.  Any way to fix it?

sc30317

---

### Post by Shinbu-Otaku on 2007-12-07
it could be that this partition is protected, hence the need for a password every time that you open it. Did you set this partition up on windows or ubuntu? If you did it on ubuntu, im pretty sure i see a thread on here that showed how to protect a partition, and they may be able to help you unprotect it. If you did it on windows, you could ask around on here but i think your best bet might be to go to a windows forum and see if they can help you unprotect it.

Sorry i cant help more

---

### Post by sc30317 on 2007-12-07
I set it up in Windows, but obviously I set up my Vista partition in Windows and it loads fine without password?

---

### Post by Ek0nomik on 2007-12-07
> **sc30317 said:**
> I set it up in Windows, but obviously I set up my Vista partition in Windows and it loads fine without password?

Can you go into /media, and run this command:

```
ls -la
```

I'm thinking the permissions are setup incorrectly for what you want to do.

---

### Post by shadow-of-sin on 2007-12-07
What does your /etc/fstab file look like?

It must have the "user" option in order for a a normal user to mount it (without root privileges)

---

### Post by sc30317 on 2007-12-07
ls -la

```

bob@bob-laptop:~$ ls -la
total 1300
drwxr-xr-x 47 bob  bob    4096 2007-12-07 12:41 .
drwxr-xr-x  3 root root   4096 2007-11-16 13:19 ..
-rwxr-xr-x  1 bob  bob   13397 2007-12-07 12:11 a.out
-rw-------  1 bob  bob    6533 2007-12-07 12:32 .bash_history
-rw-r--r--  1 bob  bob     220 2007-11-16 13:19 .bash_logout
-rw-r--r--  1 bob  bob    2313 2007-11-26 09:38 .bashrc
-rw-r--r--  1 bob  bob    2298 2007-11-16 13:19 .bashrc~
drwxr-xr-x  6 bob  bob    4096 2007-11-19 09:14 .cache
drwx------  2 bob  bob    4096 2007-11-16 18:30 .camel_certs
drwxr-xr-x 10 bob  bob    4096 2007-11-19 11:03 .config
-rw-r--r--  1 root root   1240 2007-12-05 11:37 .conkyrc
-rw-r--r--  1 root root   1239 2007-12-05 09:11 .conkyrc~
drwx------  2 bob  bob    4096 2007-12-07 12:18 .dbus-keyrings
drwxr-xr-x  6 bob  bob    4096 2007-12-07 12:41 .dc++
drwxr-xr-x  2 bob  bob    4096 2007-12-07 11:17 Desktop
-rw-------  1 bob  bob      28 2007-12-07 12:15 .dmrc
drwxr-x---  2 bob  bob    4096 2007-11-19 10:51 .easytag
drwxr-xr-x  4 bob  bob    4096 2007-11-27 21:32 .emerald
-rw-------  1 bob  bob      16 2007-11-16 18:25 .esd_auth
drwxr-xr-x  8 bob  bob    4096 2007-12-07 12:14 .evolution
drwxr-xr-x  5 bob  bob    4096 2007-11-30 11:19 .exaile
-rw-r--r--  1 bob  bob  560213 2007-12-07 11:42 Firefox_wallpaper.png
-rwxr-xr-x  1 bob  bob      61 2007-11-19 16:46 .flexlmrc
drwxr-xr-x  2 bob  bob    4096 2007-11-16 18:50 .fontconfig
drwxr-xr-x  4 bob  bob    4096 2007-11-27 23:11 .frostwire
drwx------  6 bob  bob    4096 2007-12-07 12:16 .gconf
drwx------  2 bob  bob    4096 2007-12-07 12:41 .gconfd
-rw-r-----  1 bob  bob       0 2007-12-07 12:18 .gksu.lock
drwxr-xr-x  4 bob  bob    4096 2007-11-18 17:34 .gnome
drwx------ 16 bob  bob    4096 2007-12-07 12:41 .gnome2
drwx------  2 bob  bob    4096 2007-11-16 18:31 .gnome2_private
drwxr-xr-x  2 bob  bob    4096 2007-11-29 13:28 .gpilotd
-rw-r--r--  1 bob  bob       4 2007-11-29 13:28 .gpilotd.pid
drwxr-xr-x  2 bob  bob    4096 2007-11-23 14:48 .gstreamer-0.10
-rw-------  1 bob  bob       0 2007-11-26 17:19 .gtk-bookmarks
-rw-r--r--  1 bob  bob      85 2007-11-16 18:24 .gtkrc-1.2-gnome2
-rw-------  1 bob  bob    8529 2007-12-07 12:15 .ICEauthority
drwxr-xr-x  2 bob  bob    4096 2007-11-18 17:34 .icons
drwxr-xr-x  2 bob  bob    4096 2007-12-06 21:55 Incomplete
drwxr-xr-x  3 bob  bob    4096 2007-11-18 01:08 .java
drwxr-xr-x  2 bob  bob    4096 2007-11-28 20:45 .kchmviewer
-rwxrwxrwx  1 bob  bob  409305 2007-12-06 18:29 linux.words
drwxr-xr-x  3 bob  bob    4096 2007-11-16 18:24 .local
-rw-r--r--  1 bob  bob       7 2007-12-07 12:40 ls.txt
drwx------  3 bob  bob    4096 2007-11-16 19:03 .macromedia
drwxr-xr-x  3 bob  bob    4096 2007-11-26 18:51 .maple
-rw-r--r--  1 bob  bob    3566 2007-11-26 09:19 .maple10rc
drwx------  3 bob  bob    4096 2007-11-16 18:25 .metacity
drwx------  3 bob  bob    4096 2007-11-28 13:58 .mozilla
drwxr-xr-x  3 bob  bob    4096 2007-12-07 12:14 .nautilus
-rw-r--r--  1 root root   1084 2007-11-23 17:08 .nvidia-settings-rc
drwx------  3 bob  bob    4096 2007-12-05 12:57 .openoffice.org2
drwx------ 10 bob  bob    4096 2007-12-05 10:24 .opera
-rw-r--r--  1 bob  bob     566 2007-11-16 13:19 .profile
-rw-r--r--  1 bob  bob    7215 2007-12-07 11:33 prog11.c
-rw-r--r--  1 bob  bob    7211 2007-12-07 11:21 prog11.c~
drwx------  6 bob  bob    4096 2007-12-07 12:39 .purple
-rw-r--r--  1 bob  bob   11693 2007-12-06 22:15 .pypanelrc
drwxr-xr-x  2 bob  bob    4096 2007-11-27 23:34 .qt
-rw-------  1 bob  bob    1102 2007-12-03 10:42 .recently-used
-rw-r--r--  1 bob  bob    3381 2007-12-07 12:41 .recently-used.xbel
-rw-------  1 bob  bob    1024 2007-11-18 15:51 .rnd
-rw-r--r--  1 bob  bob     613 2007-12-03 15:43 script.sh
drwxr-xr-x  2 bob  bob    4096 2007-12-06 21:55 Shared
drwx------  2 bob  bob    4096 2007-11-18 12:31 .ssh
-rw-r--r--  1 bob  bob       0 2007-11-16 18:25 .sudo_as_admin_successful
drwxr-xr-x  6 bob  bob    4096 2007-11-27 21:25 .themes
drwx------  4 bob  bob    4096 2007-11-18 01:08 .thumbnails
drwx------  2 bob  bob    4096 2007-12-07 11:17 .Trash
drwx------  2 bob  bob    4096 2007-12-03 09:03 .tsclient
drwxr-xr-x  2 bob  bob    4096 2007-11-16 18:29 .update-manager-core
drwx------  2 bob  bob    4096 2007-12-04 22:56 .update-notifier
drwxr-xr-x  3 bob  bob    4096 2007-11-27 23:36 .VirtualBox
drwxr-xr-x  2 bob  bob    4096 2007-12-02 22:44 .vnc
drwx------  2 bob  bob    4096 2007-11-16 18:51 .w3m
-rw-------  1 bob  bob     121 2007-12-07 12:15 .Xauthority
-rw-r--r--  1 bob  bob   16198 2007-12-07 12:40 .xsession-errors
drwxr-xr-x  2 bob  bob    4096 2007-12-03 16:00 .zsnes


```

/etc/fstab 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e3a3e61c-4b07-481a-8da6-b5b682f4073c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=78486D87486D44CA /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=b44cb273-86c6-4c86-bce4-255994e58178 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by Duck2006 on 2007-12-07
This may help.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mypulitzer on 2008-01-13
I don't know if the original poster has figured this out, but I'm having the same problem. I have an NTFS partition that I share between Windows and Ubuntu, and I have to enter a password to access it from Ubuntu every time I boot. The partition was formatted using Windows. I had look at the tutorial the last poster suggested, but as it is out of date, I figure there might be an easier solution for this problem. If anyone can help at all, it would be greatly appreciated.

Thanks.

---

