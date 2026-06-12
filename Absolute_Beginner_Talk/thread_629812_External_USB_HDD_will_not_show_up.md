---
title: "External USB HDD will not show up"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by WarLud on 2007-12-02
Well, I have a 100GB Seagate External USB HDD. It will not show up in Ubuntu. I plug it in and nothing happens. I have tried other USB based devices such as a flash drive and another HDD. Both work fine.

On my windows machine the hard drive works normally, and the file system on it is FAT32. (not ntfs or anything..)


Can anyone help me out on this?

---

### Post by homeskillit on 2007-12-02
maybe try sudo gparted to see if the system even recognizes it,  if it does if there's nothing on it try to reformat using gparted and use ext3   or ntfs  but install the NTFS Config Tool. Then  unplug it and plug it back in

---

### Post by WarLud on 2007-12-02
I used 'sudo gparted' and gparted did recognize it. However, i have about 50GB worth of stuff on there so I don't really want to reformat it...

---

### Post by homeskillit on 2007-12-02
I did some lookin  and I found this   

[http://ubuntuforums.org/archive/index.php/t-390147.html](http://ubuntuforums.org/archive/index.php/t-390147.html)


check it out maybe this will help

---

