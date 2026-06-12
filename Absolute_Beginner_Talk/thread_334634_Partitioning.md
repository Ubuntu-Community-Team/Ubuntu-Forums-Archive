---
title: "Partitioning?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-09
Having a slight problem when installing ubuntu, im installing of a downloaded LiveCD and when it reaches the point where im asked to choose what i want to do with my hard-drive i select the resize option, i only have the origional drive(except for that stupid windows backup one), i click Forward and the mouse changes to the timer but nothing happens, doesnt sound like the laptops using the cd or hd either. Should i just leave it for longer? Also, on a slightly more basic note, will doing this effect the stuff(apps docs music etc etc) thats already on the hd for windows? any help would be greatly appreciated! : )

---

### Post by bigken on 2007-01-09
if you have any windows partitions you must defrag them 1st 

you could also download and burn gparted use this to free some space on your hdd ;)

---

### Post by Sef on 2007-01-09
> i click Forward and the mouse changes to the timer but nothing happens, doesnt sound like the laptops using the cd or hd either. Should i just leave it for longer?

How long have you waited?

> Also, on a slightly more basic note, will doing this effect the stuff(apps docs music etc etc) thats already on the hd for windows?

Should not affect it at all, if all goes well.  **Back up** your files first.  Nothing is 100% guaranteed.

If it don't work with the Live CD, then try the alternate cd.  It is text based but very easy to install.  Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").

---

### Post by bigken on 2007-01-09
oops forgot to mention backup anything important

---

### Post by teaker1s on 2007-01-09
gparted live boot iso may help, as said before scan disc and defrag-also first time you boot windows after let it scan disk or you will blue screen esp on xp

---

### Post by bigken on 2007-01-09
> **teaker1s said:**
> gparted live boot iso may help, as said before scan disc and defrag-also **first time you boot windows after let it scan disk or you will blue screen esp on xp**

does it ? never has on me 8)

---

### Post by housam on 2007-01-09
Do your partitions manually. its better to resize your xp partition by yourself.
IMPORTANT:while defraging windows partition try to locate the green mark (the unmovable data)which is windows system files and i.e. if it is in the middle of the partition , be careful not to shrink the partition to behind that limit or you will damage your windows system files.
For Gparted , it is on the live CD . set your computer to boot from the cd-rom then insert the CD and click system >> admin. >> Gnome partition editor.
you have to create two partitions,( / ) for root & (swap).

---

