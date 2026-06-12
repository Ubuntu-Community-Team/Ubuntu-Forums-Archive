---
title: "Heeelp Vaio doesnt let me do the partition!!!"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by flavio newbie on 2007-05-30
i DON'T KNOW WHATS WRONG WITH MY COMPUTER, but my Vaio VGN-FS830/W doesnt allow the partition. It doesnt work with g parted and it doesnt work with Partition magic. With G parted ubuntu just freezes and i have to reset, with partition magic it says it will do it but then it doesnt.

---

### Post by Inxsible on 2007-05-30
What is the error that you get with GParted?
 
What other OS - if any - is installed on your machine?

---

### Post by cotcot on 2007-05-30
Have you tried the Gparted LiveCD.

---

### Post by flavio newbie on 2007-05-30
With Gparted it freezes, the computer does not work anymore, and there is still only windows on it. G parted i use it while trying the installation of ubuntu. The cd is not corrupted, i used it today for another machine

---

### Post by Inxsible on 2007-05-30
can you put in your live cd and then open a terminal
 
Applications --> Accessories --> Terminal and enter this command :
 
```
sudo fdisk -l
```
 
Also if you could show us a screenshot of your Gparted before you hit install, so that we can have a look at how your drives are listed or what partitions exist, mebbe we can help you out better.

---

### Post by flavio newbie on 2007-05-30
ok ill do that, i need 10 mins

---

### Post by flavio newbie on 2007-05-30
here is the screenshot. The first little partition is the hidden one for the recovery, typical of vaio.

---

### Post by Inxsible on 2007-05-30
Which Windows are you using?
 
Did you perform a defrag thru windows before trying to install Linux ? Maybe you have a fragmented drive and so its not able to partition it correctly
 
I would say perform 3-4 defrags one after the other and immediately come to installing linux.
 
See if that works.

---

### Post by flavio newbie on 2007-05-30
The disk has been defragmented, and the os is windows xp sp2. and btw when i look at the disk analysis its perfectly clean for the 40 gb, and i want only ten of them

---

### Post by flavio newbie on 2007-05-30
this time it gave me an error

---

### Post by flavio newbie on 2007-05-30
attachment

---

