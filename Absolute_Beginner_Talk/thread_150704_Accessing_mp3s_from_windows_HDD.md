---
title: "Accessing mp3s from windows HDD"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by TuckWat on 2006-03-26
I just got a new HDD and installed dapper on a partition and am trying to figure out how to play MP3's from another hard drive (Windows NTFS).  I've tried with amarok and XMMS by trying to add /tmp/disks-conf-hdc1/ but it is having trouble adding them.  I did install mp3 codecs through the wiki but couldn't find any relative information.  

Thanks guys

---

### Post by ajgreeny on 2006-03-26
If you simply mount your windows drive in the usual way, see [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions) surely the mp3s will play with whatever you have set as default to play mp3 files.
This is certainly the case in breezy; I've just checked it and xmms does a great job.

---

### Post by sn123 on 2006-03-26
[QUOTE=TuckWat]I just got a new HDD and installed dapper on a partition and am trying to figure out how to play MP3's from another hard drive (Windows NTFS).  I've tried with amarok and XMMS by trying to add /tmp/disks-conf-hdc1/ but it is having trouble adding them.  I did install mp3 codecs through the wiki but couldn't find any relative information.  

Thanks guys[/QUOTE]
mount your windows ntfs partition and then access the mount directory using xmms.
Step by step guide:
```

1. open a terminal console
2. $ sudo mkdir /media/windows
3. $ sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
Change /media/windows to any directory that you like and replace /dev/hda2 with your windows partition. Use nautilus to browse the contents of /media/windows and all your window's folder should show up including the mp3 folders.

S

---

### Post by TuckWat on 2006-03-26
Ok, when I run the the command, I get this message: 

```
mount: /dev/hdc1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hdc1 is mounted on /tmp/disks-conf-hdc1
```

And in XMMS when I try to browse the folder /tmp/disks-conf-hdc1, it doesn't show any files.

In System -> Administration -> Disks, and in the windows partition tab, I can click browse and see all of the files but in Nautilus it says: > You do not have the permissions necessary to view the contents of "disks-conf-hdc1"

---

### Post by arnieboy on 2006-03-26
```
sudo gedit /etc/fstab
```
find the ntfs partition which u want read permissions on and look for the word "**defaults**" in the same line.
replace that with the following:
> **nls=utf8,umask=0222**
save and exit and reboot.

---

### Post by TuckWat on 2006-03-26
Ok, I unmounted the partition using

sudo umount /tmp/disks-conf-hdc1

then mounted it again to /media/windows/ and everything is working perfectly.

Thanks everyone for the help!

---

### Post by sn123 on 2006-03-26
[QUOTE=TuckWat]Ok, I unmounted the partition using

sudo umount /tmp/disks-conf-hdc1

then mounted it again to /media/windows/ and everything is working perfectly.

Thanks everyone for the help![/QUOTE]

follow arnieboys' instructions to make ntfs partition readable on every boot, otherwise you'll have to manually unmount the ntds partition from /tmp/disks-conf-.... and mount it again everytime you reboot ubuntu.

S

---

