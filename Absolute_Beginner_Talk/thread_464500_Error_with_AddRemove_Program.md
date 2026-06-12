---
title: "Error with Add/Remove Program"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by BeezyF90 on 2007-06-04
Whenever I try to download something through add/remove programs half the time I'll recive the message 
Please insert the disk labeled:
Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)
in drive /cdrom/

even though the CD is inserted into the drive, I can even see it on the desktop 
also some downloads will work fine while others pop this message up
help please

---

### Post by regomodo on 2007-06-04
go through

system/software sources/Third party software

Do you have  a cd-rom entry?

---

### Post by BeezyF90 on 2007-06-04
whats a cd rom entry

---

### Post by regomodo on 2007-06-05
ok. take a look at mine. do you have any more than 2 entries? You shouldn't need the CD for updates. It's all done via the web

---

### Post by BeezyF90 on 2007-06-05
I only have one entry and when ever I try to add one It wont let me, also it doesnt seem to sense my cd rom drives, the odd thing is I can see them through the desktop but when It tries to read a cd it doesnt read anything

---

### Post by Nekiruhs on 2007-06-05
Post your sources.lst. please 
```
cat /etc/apt/sources.list | grep cdrom0
```
also post your fstab 
```
cat /etc/fstab | grep cdrom0
```
Thanks.

---

### Post by BeezyF90 on 2007-06-05
neal@ubuntustudio:~$ cat /etc/fstab | grep cdrom0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Nekiruhs on 2007-06-05
So it looks like fstab is reconigzing the fact that the CD Drive is there. Im going to need the sources.lst too.

---

### Post by BeezyF90 on 2007-06-05
neal@ubuntustudio:~$ cat/etc/apt/sources.list | grep cdrom0
bash: cat/etc/apt/sources.list: No such file or directory

---

### Post by Nekiruhs on 2007-06-05
> **BeezyF90 said:**
> neal@ubuntustudio:~$ cat/etc/apt/sources.list | grep cdrom0
bash: cat /etc/apt/sources.list: No such file or directory
add a space, cat is a command, just copy and paste.

---

### Post by BeezyF90 on 2007-06-05
neal@ubuntustudio:~$ cat /etc/apt/sources.list | grep cdrom0
neal@ubuntustudio:~$ 
I tired it numerous times and it never game me an answer :(

---

### Post by Nekiruhs on 2007-06-05
> **BeezyF90 said:**
> neal@ubuntustudio:~$ cat /etc/apt/sources.list | grep cdrom0
neal@ubuntustudio:~$ 
I tired it numerous times and it never game me an answer :(
And thats where your issue is. Basically, that command i gave you, opened your sources.list (Where ubuntu looks for repositories) checked to see checked to see if your CD drive was mentioned, and should have returned a line or two. You need to add your cd drive as a repo. Just type ```
sudo apt-cdrom add
``` and that should fix it.

---

### Post by BeezyF90 on 2007-06-05
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.

I dont know why it does this espcially when I can see the CD on the desk top

---

