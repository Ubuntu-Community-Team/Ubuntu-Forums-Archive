---
title: "mount my existing hdd in ntfs format"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by redenjaja on 2005-10-02
i've just installed breezy badger here in my office. this pc has 2hdd which are both in ntfs format, i would like to browse for the files from those hdd but i cant mount them. here's the setup of my pc in xp...

drive c: 20gig (ntfs)
drive d: 20 gig (ntfs) i partitioned this drive using systemrescuecd and in this drive is where i             installed ubuntu. now how can i mount those ntfs drives?

i tried this:
batangascontrolroom@ubuntu:~$ sudo mkdir /media/windows
Password:
mkdir: cannot create directory `/media/windows': File exists
batangascontrolroom@ubuntu:~$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: special device /dev/hda1 does not exist
batangascontrolroom@ubuntu:~$

---

### Post by Ampersand on 2005-10-02
Since you're using Breezy, there should be a 'Disks' entry in the System - Administration menu (If I remember correctly, I'm not in Gnome at the moment). You can use that to mount other drives.

---

### Post by mlomker on 2005-10-02
What is the output of **sudo fdisk -l**?

---

### Post by redenjaja on 2005-10-02
yipee! i finally mounted it!:D :D :D

---

