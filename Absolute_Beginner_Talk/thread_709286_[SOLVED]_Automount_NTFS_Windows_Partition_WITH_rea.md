---
title: "[SOLVED] Automount NTFS Windows Partition WITH read and write capability"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Amivit on 2008-02-27
I managed to make my windows partition auto mount, but only with read permissions.
Now if I ```
gksudo nautilus
```, I can write to the windows partition,
so it definitely works. 

Is there any way to do this? Thanks a lot ! :)

---

### Post by glennric on 2008-02-27
You could install the package "ntfs-3g" and then add the line
```
/dev/??? /mount/point     ntfs-3g    defaults,locale=en_US.utf8,uid=1000,gid=1000 0       1

```
to fstab, where ??? is the device name of the ntfs partition.

Edit:  I should read posts more carefully before replying.  You want read only not read/write.  Just edit fstab and add "ro" to the options list of your existing line for the ntfs partition.

---

### Post by Amivit on 2008-02-27
EDIT: I should describe my post better so people understand lol .

I DO want read/write capability. And I actually have it already.

But the problem is I only have read/write capability as ROOT.
I want to auto mount the partition with read/write capability WITHOUT
having to be ROOT.

So far I've been able to auto mount the partition but only with read permissions.
But I want auto mount WITH read / write permissions ! :)

---

### Post by sisco311 on 2008-02-27
please post the output from:
```
ls -al /media
id
cat /etc/fstab
```

---

### Post by kaginken on 2008-02-27
Also, please tell us what version of ubuntu you are using.  Gutsy Gibbon comes with built in NTFS support...makes it a little easier.

---

### Post by Amivit on 2008-02-27
Sorry I forgot. I use Ubuntu 7.10 Gutsy Gibbon, fully updated.

```

[COLOR="Red"]gormsbo@gormsbo-desktop:~$ ls -al /home[/COLOR]
total 12
drwxr-xr-x  3 root    root    4096 2008-02-26 21:41 .
drwxr-xr-x 22 root    root    4096 2008-02-27 15:35 ..
drwxr-xr-x 35 gormsbo gormsbo 4096 2008-02-27 16:03 gormsbo
[COLOR="Red"]gormsbo@gormsbo-desktop:~$ id[/COLOR]
uid=1000(gormsbo) gid=0(root) groups=0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev)
[COLOR="Red"]gormsbo@gormsbo-desktop:~$ cat /etc/fstab[/COLOR]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=892df79c-7ae2-43e7-bbb8-2cbe8e32e207 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8aa6ee8a-565d-47aa-bf64-7364d225ae4f none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

```

---

### Post by sisco311 on 2008-02-27
and the output from:
```
ls -al /windows
```

---

### Post by Amivit on 2008-02-27
```

[COLOR="Red"]gormsbo@gormsbo-desktop:~$ ls -al /windows[/COLOR]
total 786911
dr-xr-xr-x  1 root root     12288 2008-02-26 20:23 .
drwxr-xr-x 22 root root      4096 2008-02-27 15:35 ..
-r-xr-xr-x  1 root root         0 2007-11-29 19:50 AUTOEXEC.BAT
-r-xr-xr-x  1 root root      4952 2003-04-25 14:00 Bootfont.bin
-r-xr-xr-x  1 root root       211 2007-11-29 22:33 boot.ini
-r-xr-xr-x  1 root root         0 2007-11-29 19:50 CONFIG.SYS
dr-xr-xr-x  1 root root      4096 2008-02-21 19:42 Documents and Settings
dr-xr-xr-x  1 root root         0 2008-02-26 19:27 Downloads
dr-xr-xr-x  1 root root         0 2008-01-13 17:59 ijji
-r-xr-xr-x  1 root root         0 2007-11-29 19:50 IO.SYS
-r-xr-xr-x  2 root root         0 2008-01-05 22:30 logwmemory.bin
-r-xr-xr-x  1 root root         0 2007-11-29 19:50 MSDOS.SYS
-r-xr-xr-x  1 root root     47564 2007-11-29 22:27 NTDETECT.COM
-r-xr-xr-x  1 root root    250048 2007-11-29 22:27 ntldr
dr-xr-xr-x  1 root root         0 2007-12-06 14:34 NVIDIA
-r-xr-xr-x  1 root root 805306368 2008-02-26 20:23 pagefile.sys
dr-xr-xr-x  1 root root     16384 2008-02-26 19:30 Programmer
dr-xr-xr-x  1 root root      4096 2008-02-22 16:59 RECYCLER
-r-xr-xr-x  2 root root         0 2008-02-21 21:31 regdump.arm9.txt
dr-xr-xr-x  1 root root     12288 2008-01-05 22:29 Soldat
-r-xr-xr-x  2 root root       268 2007-12-03 18:14 sqmdata00.sqm
-r-xr-xr-x  2 root root       268 2007-12-04 17:07 sqmdata01.sqm
-r-xr-xr-x  2 root root       268 2007-12-06 14:02 sqmdata02.sqm
-r-xr-xr-x  2 root root       268 2007-12-07 16:04 sqmdata03.sqm
-r-xr-xr-x  2 root root       268 2008-02-23 23:06 sqmdata04.sqm
-r-xr-xr-x  2 root root       268 2008-02-24 20:54 sqmdata05.sqm
-r-xr-xr-x  2 root root       268 2008-02-25 19:12 sqmdata06.sqm
-r-xr-xr-x  2 root root       268 2008-02-25 20:35 sqmdata07.sqm
-r-xr-xr-x  2 root root       268 2008-02-25 21:50 sqmdata08.sqm
-r-xr-xr-x  2 root root       268 2008-02-26 19:33 sqmdata09.sqm
-r-xr-xr-x  2 root root       244 2007-12-03 18:14 sqmnoopt00.sqm
-r-xr-xr-x  2 root root       244 2007-12-04 17:07 sqmnoopt01.sqm
-r-xr-xr-x  2 root root       244 2007-12-06 14:02 sqmnoopt02.sqm
-r-xr-xr-x  2 root root       244 2007-12-07 16:04 sqmnoopt03.sqm
-r-xr-xr-x  2 root root       244 2008-02-23 23:06 sqmnoopt04.sqm
-r-xr-xr-x  2 root root       244 2008-02-24 20:54 sqmnoopt05.sqm
-r-xr-xr-x  2 root root       244 2008-02-25 19:12 sqmnoopt06.sqm
-r-xr-xr-x  2 root root       244 2008-02-25 20:35 sqmnoopt07.sqm
-r-xr-xr-x  2 root root       244 2008-02-25 21:50 sqmnoopt08.sqm
-r-xr-xr-x  2 root root       244 2008-02-26 19:33 sqmnoopt09.sqm
dr-xr-xr-x  1 root root         0 2008-02-21 20:25 studio
dr-xr-xr-x  1 root root      4096 2007-11-30 03:06 System Volume Information
dr-xr-xr-x  1 root root         0 2008-02-13 18:02 $VAULT$.AVG
dr-xr-xr-x  1 root root    110592 2008-02-26 19:26 WINDOWS


```
ps, Very thankful for the replies so fast and people willing to help :)

---

### Post by sisco311 on 2008-02-27
backup your fastab:
```
sudo cp /etc/fstab /etc/fstab-backup
```change the last line in fstab to:

> 
/dev/hda1 /windows ntfs defaults,umask=007,gid=46 0 1

and set the owner of /windows:
```

sudo chown -R root:plugdev /windows

```
remount the partition:
```
sudo umount /dev/hda1
sudo mount -a
```

---

### Post by Amivit on 2008-02-27
Perfect. It works. Thanks a lot. And take a look at this
[http://www.google.com/search?hl=da&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=fZj&q=linux+automount+windows+partition&btnG=S%C3%B8g&meta=]("http://www.google.com/search?hl=da&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=fZj&q=linux+automount+windows+partition&btnG=S%C3%B8g&meta=")
(: - that went pretty fast . 
Oh and by the way, great signature. Made me lol :D .

---

