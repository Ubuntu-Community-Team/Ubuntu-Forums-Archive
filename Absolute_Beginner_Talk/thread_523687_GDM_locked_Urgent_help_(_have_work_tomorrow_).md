---
title: "GDM locked Urgent help ( have work tomorrow )"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-08-12
and my work documents are inside the machine !!!!

I received a low disk space warning, so I started to back up things but it froze ,,so I killed the back up program with X kill

later on after watching a movie I restarted the computer, except it didnt let me in

I got to the username password  (log in page) and I got an error message

 Translated from Japanese it says 

[SIZE="2"]  GDM cannot allow the file, maybe the disk is full  and the home folder has no authentication to write to [/SIZE]

Can someone please help ASAP ,,, as I need some file on the disk for work tomorrow 

Kind regards in advance Stephen

---

### Post by Saner on 2007-08-12
you could boot from A Live CD and free up some space.


O maybe you can boot to console if you use the "Recovery mode" (dont know if this will work)

---

### Post by basilwatson on 2007-08-12
good Idea will try that ,,,,,,runs offf,,,,not crying so much ,,,,,,,

thanks 

Stephen

---

### Post by shearn89 on 2007-08-12
Do you have a seperate /home partition?

---

### Post by basilwatson on 2007-08-12
> **shearn89 said:**
> Do you have a seperate /home partition?

No ( I suspect I should)   I have 3 partitions hda4 Hda 2 hda1 and swap 

hda 2 is full  I am just ( famous last words ) resizing them hopefull that will do it 

Question how do you make the home folder a parttion ??

Stephen

---

### Post by por100pre1 on 2007-08-12
> **basilwatson said:**
> No ( I suspect I should)   I have 3 partitions hda4 Hda 2 hda1 and swap 

hda 2 is full  I am just ( famous last words ) resizing them hopefull that will do it 

Question how do you make the home folder a parttion ??

Stephen

A separate /home partition can be useful but IMHO the best way is just to make backups of your  /home folder on an external HDD. Grsync can help you on that. Keep in mind that Ubuntu, as any other OS, needs a good amount of disk space to work, so try to be generous when allocating disk space to your Ubuntu partition(s). :)

---

### Post by basilwatson on 2007-08-12
> **por100pre1 said:**
> A separate /home partition can be useful but IMHO the best way is just to make backups of your  /home folder on an external HDD. Grsync can help you on that. Keep in mind that Ubuntu, as any other OS, needs a good amount of disk space to work, so try to be generous when allocating disk space to your Ubuntu partition(s). :)

Ta 

all solved now , I repartitioned then sudo apt-get clean 

as well as deleted all the crap ,,,,, !!!!  ( I bet u Ill need some of it again !) 

Thanks all for the help 

Stephen

---

