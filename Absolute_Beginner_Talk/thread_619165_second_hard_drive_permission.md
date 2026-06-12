---
title: "second hard drive permission"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Edgy Eft Fan on 2007-11-21
OK, ive been at this ubuntu game for about a year or two and im still struggling with commands and codes to do certain things.
ive read the similar threads to this question and im no wiser... sorry to start another one but i get lost trying the other suggestions
call me stupid if u like but i just cant seem to get a grip of some ubuntu linux procedures.
Im using feisty 7.04 which is excellent, i tried gutsy 7.10 but had a few probs with open office which i use a lot so that was out. i get fantastic stability using feisty even using beryl.
My problem is this.
I have installed a second 160gb sata hard drive which i would like to save my personal pictures / music / videos on.
i have it partitioned in 2 and formatted ext3. i can see and mount both partitions but cant write to any of them. There is no windows or nfts involved, simply ubuntu. I'd like to acces the second hard drive as storage to avoid the need to back up to dvd's all the time, if i need to put in a password everytime i want to write to it.. all the better and secure
the partitions are named sdb1 and sdb2.
is it possible for someone to spell out step by step how to go about this?
please please :)
thanx in advance
Garry

---

### Post by justleen on 2007-11-21
the quickest way is to simple give your main user write access to the drive.
```

sudo chown -R user:user /media/drive 
```

offcourse, change to you usernam,e and diskname

---

### Post by Edgy Eft Fan on 2007-11-21
im gob smacked.... it actually worked!!
thank you , you have no idea how long ive been pulling out what little hair i have to get this working
thank you

---

### Post by justleen on 2007-11-21
no problem :)

---

### Post by Josephr on 2008-04-04
Not wanting to start another thread but I have the same problem as this other user, however the suggested method to resolve this does not work for me, I have played with linux on and off for many years and am still  none the wiser, Im one of these many peeple that adore gui's and avoid like the plague cli's, soo in as graphical detail as possible Ill begin lol

Ok computer yesterday was running windows and was working a treat, installed linux and upgraded today to ubuntu 7.10.  All OS installed in first drive, second drive was ignored. Ok installed Gparted a partition manager and converted second drive with the following details:

Partition: /dev/hdb1 (graphical image of a padlock)    Filesystem: ext2  Mountpoint: /media/disk  Size 37.27Gb  Used 647.24Mb  Unused: 36.64Gb Flags: boot

Ok now starting Disk file browser and as you would expect the home folder and file system tree is present, at the bottom is disk which is the newly formatted and partitioned drive. 

I can click on this and present in the drive is folder Lost+found with group:root owner: root and permissions drwx
I Try to copy or cut a file into the drive and with menu the paste function is disabled.  In the tree where disk is located I right click on disk and click on properties, in the permissions tab the owner is root, the group is root and as far as folder accesses are concerned they are all greyed out.

Now this is where I get stupid, because root as far as I was concerned was never part of the user creation, I presume this is some sort of default setup, again I tried above and nothing happened.

Please please please can someone shed some light on this for me, as Im still getting to grips with the filesystem in linux

Thank you

---

