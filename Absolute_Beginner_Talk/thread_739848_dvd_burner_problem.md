---
title: "dvd burner problem"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by mannafran on 2008-03-30
hello my community! i'm still fairly new to ubuntu and linux. i have felt cleansed since installing a real operating system. but i am still windowcentric i guess and finding it a bit confusing and VERY time consuming to work out some problems i'm having. as a few posts have said ask one thing at a time..... i have a dvd burner and a cd player in my machine. both are recognized, both read any given cd, but the dvd, although it sees the same files, can't open them...? for example mp3's or mpegs play ok thru the cd player, yet in the dvd burner, when you select an mp3 it opens a dialog box that says something like- this is a text file that i can't open....?
of course all my dvds with files, music and movies on them are the same, files won't open, but i can't test them on the cd player of course. all discs are ok in the windoze laptop i have....?
thanx in advance

---

### Post by c-ron on 2008-03-30
Can you paste the contents of your /etc/fstab file here please?

---

### Post by mannafran on 2008-03-30
> **c-ron said:**
> Can you paste the contents of your /etc/fstab file here please?

yes if i knew what that meant... well i did give that terminal thingy a go, - pasted those words in and enter -but it said permission denied...

---

### Post by cookiemonster0774 on 2008-04-02
at the command line type 'sudo gedit /etc/fstab' it will ask for a password 
it will then open a text editor with the contents of fstab. copy and paste those here. then maybe someone can help. Good luck.

---

### Post by mannafran on 2008-04-13
i've been away and i couldn't get the command line to work, but i just did it again and it finally worked,
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ae5244ce-3da5-439d-9c44-4efd10983c0a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=094db8c6-459a-43c7-ae8b-363191d015ff none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

hope this means something to someone..

---

