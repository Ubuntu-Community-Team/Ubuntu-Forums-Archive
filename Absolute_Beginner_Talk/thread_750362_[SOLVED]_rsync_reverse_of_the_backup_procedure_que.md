---
title: "[SOLVED] rsync reverse of the backup procedure question"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by bred on 2008-04-09
Hello,
I used this tutorial [http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")
in oder to backup my files(my documents,music etc)  about 15Go
I did this
[COLOR="Blue"]rsync -av /home/pc /media/disk-2 [/COLOR]

knowing that pc - is my user name and disk-2 is my external HDD

everything went well...I have my backup

now the big question pls-
I want to format my pc and to reinstall ubuntu gutsy,
 then I want to reverse all my backup files (my documents, music etc) from my external HDD back to my fresh install ubuntu 7.10
but HOW to reverse?
thx in advance

---

### Post by bred on 2008-04-09
[COLOR="Blue"]I can belive it,
no one use rsync?
come on...[/COLOR]

---

### Post by vanadium on 2008-04-09
Surely you expect very quick answers ... To reverse the action, swap the source and destination.

rsync -av /home/pc /media/disk-2 

becomes:

rsync -av /media/disk-2 /home/pc 

Quite obvious, isn't it? (make sure you create the directory"/home/pc" before running the rsync command)

---

### Post by aysiu on 2008-04-09
Really you don't even need to use *rsync* to restore the backup. You can just copy and paste the files in the normal file browser way.

---

### Post by bred on 2008-04-10
> **vanadium said:**
> Surely you expect very quick answers ... To reverse the action, swap the source and destination.

rsync -av /home/pc /media/disk-2 

becomes:

rsync -av /media/disk-2 /home/pc 

Quite obvious, isn't it? (make sure you create the directory"/home/pc" before running the rsync command)

thx dude !!!

---

