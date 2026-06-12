---
title: "About mounting cdrom/cdrecorder drives"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by jis on 2006-07-20
Why do I have "udf,iso9660" as third column for cdrom in /etc/fstab and not "auto" (In [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) you are advised to use "auto" there.)

Why do I have "cdrom" link in "file system" folder and another "cdrom" link in /media/ folder? (The target of the former is the latter and the target of the latter is "cdrom0".)

I wish I could mount my primary optical drive as /media/cdrw and the secondary drive as /media/cdrom (so that the names correspond the functions of each drive). Does this make sense and do I have to change the previously mentioned links?

---

### Post by ironfistchamp on 2006-07-20
Ok I shall give this a shot. I am still a total n00b but I might get it.

1) Not a clue. Does it affect the performance? If not leave it. If it does someone else might know what to do

2)I suppose having a link to it in the / makes it easier. If you are in the terminal and are in / maybe you don't what to cd into a longer folder. It is easier to just type cd cdrom0. I don't really know but it isn't a problem is it?

3)You could create a new di in /media  called cdrw and mount it. if you want it mounted at startup you need to edit your fstab (/etc/fstab). If you do so be INSANELY careful. You really don't want to mess up your fstab. I have and it went crazy. 

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

That is the line I have for my DVDRW. I think the next optical drive would be hdd. You would mount it the same way just changing /media/cdrom0 to /media/cdrw. I think this is right. I am no expert. Be careful and I hope this helped.


Ironfistchamp

---

### Post by jis on 2006-07-21
2) Is it safe to delete/rename/modify the (chained) soft links to cdrom0, does linux (and xubuntu) assume these exists by that name "cdrom"? If I would change the name of the primary optical drive from cdrom0 to cdrw, cdrom links wouldn'd point anywhere so I would have to modify/delete them. On the other hand, if I mount the secondary optical drive as cdrom, symbolic (soft) links named as cdrom pointing to cdrw would be missleading.

---

### Post by ironfistchamp on 2006-07-21
I supopse you could rename them or create new ones to new places. Just remember what they looked like beforehand so you can change them back if necessary.

---

