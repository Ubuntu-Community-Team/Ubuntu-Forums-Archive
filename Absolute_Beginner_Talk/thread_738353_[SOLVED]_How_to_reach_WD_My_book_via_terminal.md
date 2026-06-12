---
title: "[SOLVED] How to reach WD My book via terminal"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by cemlouis on 2008-03-28
Hello,

I can reach my WD My book via Dolphin file manager and easily browse, write - delete files... How can I do this with a terminal window? 

Thank you,

---

### Post by Het Irv on 2008-03-28
What is the file path in Dolphin, if you can find that you should be able to use,
```
cd /whatever/the/file/path/is
```
that command will put you in the Drive's main folder

---

### Post by louieb on 2008-03-28
Assuming it got mounted when you plugged  it in. 1st thing you need to know is the mount point.  To list you mounts the command is  ```
mount 
```Now you know the path to the files on the WD drive. You use the cp (copy) mv (move) rm (remove), These commands have a lot of options suggest you look at man <command> for a list of options. 

Might try browsing arount this site too. [tuXfiles - the Linux newbie help files, tutorials, and tips]("http://www.tuxfiles.org/")

---

### Post by cemlouis on 2008-03-28
> **louieb said:**
> Assuming it got mounted when you plugged  it in. 1st thing you need to know is the mount point.  To list you mounts the command is  ```
mount 
```Now you know the path to the files on the WD drive. You use the cp (copy) mv (move) rm (remove), These commands have a lot of options suggest you look at man <command> for a list of options. 

Might try browsing arount this site too. [tuXfiles - the Linux newbie help files, tutorials, and tips]("http://www.tuxfiles.org/")

Hello louieb,

Please see below:

> 
/dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower)
louis@backup:/$ cd media
louis@backup:/media$ cd My Book
bash: cd: My: No such file or directory
louis@backup:/media$ cd ..
louis@backup:/$ cd /dev
louis@backup:/dev$ cd sda1
bash: cd: sda1: Not a directory
louis@backup:/dev$   


Several tries unable to reach it...
Any ideas?

---

### Post by Inxsible on 2008-03-28
since My Book has a space in it you need to use
```
 cd /media/"My Book"
``` or ```
 cd "/media/My Book"
```As a side note, I would avoid naming folders and drives with spaces in it. Just saves you the hassle of using quotes in the commands

---

### Post by cemlouis on 2008-03-28
> **Inxsible said:**
> since My Book has a space in it you need to use
```
 cd /media/"My Book"
``` or ```
 cd "/media/My Book"
```As a side note, I would avoid naming folders and drives with spaces in it. Just saves you the hassle of using quotes in the commands

Sorry for this newbie question :) "Quotes"

---

### Post by Inxsible on 2008-03-28
> **cemlouis said:**
> Sorry for this newbie question :) "Quotes"No problem. Everyone's a newbie at one point of time.

Make sure you mark your thread solved :)

---

