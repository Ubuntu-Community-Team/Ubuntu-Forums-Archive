---
title: "drive dissapered in windows"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by smurf killer on 2007-03-30
hi i recently installed ubuntu, i use my windows drive to listen to music and as far as i remember i haven't used that drive to anything in the installation of ubuntu (but im not sure) but now it dissapered from windows and i can't run any program from it. when i try to go into this computer -> administer and then look at my drives it says that it is a windows format but unknown partition. why is that, is there anything i can do about it?

---

### Post by nixclusive on 2007-03-30
from what I understand from your description; you used to have a drive that contained music files and now after installing ubuntu that drive is missing i.e. inaccessible from windows.. right?

---

### Post by smurf killer on 2007-03-30
yes sorry for the not so good description. but yes, and im not sure if i used that disk for swap files

---

### Post by Gina on 2007-03-30
Hope you backed up all your music files - if not I think you've probably lost them if you did use it for swap.

I'm a newbie to Ubuntu but not to computers in general and I always recommend backing up everything of any value - particularly if messing with partitions or installing something that uses it's own partition.  Bit late for that advise I know :(  (But maybe someone thinking of installing Linux is reading this)

---

### Post by dptxp on 2007-03-30
I think that you can check the status by with GPARTED or QPARTED. You can carry out further action too, but be careful not to take any action unless you are sure. (like formatting).

You will find QPARTED in installed OS in the menus, GPARTED in installation disk. You can even add GPARTED to installation, I forget how.

---

### Post by smurf killer on 2007-03-30
okay thanks for the advices. but hopefully i can backup my music and other things from ubuntu. but there isn't any of you who knows how i can make it work in windows again?

---

### Post by dptxp on 2007-03-30
First see if you got your data, most probably it is gone. You do not see it in Windows, so you have maybe formated the drive.

Windows reads FAT32 partitions, so does UBUNTU. you can access by both, easily from Ubuntu if you have partitioned and made that drive while installing UBUNTU.

EXt3 partitions can also be read by Windows, you need to intall (I forget what) in Windows.

So you can read data from any drive (dunno about the Ubuntu root and swap) from either OS, can write too. Ubuntu has problems reading NTFS partitions, you can read with some efforts, but can not write.

---

### Post by docshawnc on 2007-03-30
To read the ext2 and 3 systems from windows try looking here [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by Gina on 2007-03-30
As neither Linux nor Windows sees your old Windows partition I think you have lost it.  But some of the lost files might be recoverably using a System Rescue/Recovery CD. 

I have yet to try this on a data partition one of my Windows apps marked as unformatted a few days after installing Ubuntu (in a recovered part of it after resizing).  it was OK after install but died later.  I have downloaded an ISO file and burnt it to CD-R ready to use but haven't had the time to try it, so can't tell you how well it works, I'm afreaid..  [http://www.sysresccd.org]("http://www.sysresccd.org") is the website.

---

### Post by smurf killer on 2007-03-30
the weird thing is that i have no problems using it with ubuntu, and i can see the drive from administer from the this computer menu

---

### Post by smurf killer on 2007-04-06
i found out that another of my harddrives available in linux also which i thought was dead. is it just my windows which is going down or where is the problem?

---

