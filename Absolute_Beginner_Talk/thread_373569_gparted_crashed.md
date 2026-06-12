---
title: "gparted crashed"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-01
no matter what i did i couldnt make a second partition that include swap and root. anything i did makes next to the new partition name this sign: ! .  and  an orange triangle . now im in xp and my second partition "d:" is totally disapered . im really desperate trying to install for hours and i dont understand why all this mess. i thought its much simple.

---

### Post by oilchangeguy on 2007-03-01
probably the way to go is to select the option that allows ubuntu to use the largest free space. this will not remove you xp install. if say you have a 40gb hard drive you'll most likely end up with xp having around 18gb, and ubuntu 22gb. don't get all wraped up in manually creating ubuntu partitions. it knows what to do all by itself when it's installing. anyway if you've got a computer that has to tap into swap/virtual memory, you've got a computer with problems.

---

### Post by Duck2006 on 2007-03-01
Is the second hard drive formated as ntfs and does it have files on it?

---

### Post by oilchangeguy on 2007-03-01
duck, the user says they are trying to make a second partition. nothing about a second hard drive. all the user has to do is allow ubuntu to do it's thing, and it will properly handle creating the partition.

---

### Post by Duck2006 on 2007-03-01
Ok sorry
Did they defrag the drive befor they tryed to partition the drive?

---

### Post by fanny on 2007-03-01
o.k listen guys. i didnt do anything special before i just put the cd and trying to install. as i said now i cant see my d drive ( i have c 40g and d 40g also ) . after the oilchangeguy comment i restart and tried again and i have only the next 3 options:
1) resize IDE2 master . partition #1 (hdc1) and use freed space. ( remember i dont wont to install in c )
2) erase entire disk........... (no)
3)manually edit ..............(doesnt work for me i tried until the crashed )

---

### Post by Segovia on 2007-03-01
Sounds like gparted may have corrupted your partition table.  Have a look at this [bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/48229").

---

### Post by fanny on 2007-03-01
so what should i do?

---

### Post by Duck2006 on 2007-03-01
May be you sould download gparted live cd and use that to partition your drive.
 

> Segovia posted
Sounds like gparted may have corrupted your partition table. Have a look at this bug on launchpad.

---

### Post by fanny on 2007-03-01
where do i download it?

---

### Post by Duck2006 on 2007-03-01
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by fanny on 2007-03-01
is it possible to use it through xp ? ( if not how will i use it ?)

---

### Post by Duck2006 on 2007-03-01
Once your downloaded gparted you burn it to a cd and then boot it up. If you want to partition your drive in windoze you will have to use something live partition magic.

---

