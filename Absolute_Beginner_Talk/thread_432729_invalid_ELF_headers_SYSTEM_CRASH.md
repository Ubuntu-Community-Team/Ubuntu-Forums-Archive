---
title: "invalid ELF headers SYSTEM CRASH"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by egoldtech on 2007-05-04
Hi, 
Im using Ubuntu 6.06 on mi THinkpad laptop.
I can get to the system login, but after out my user password, i get a system error, and when I click on details, I see some common libraries have a invalid ELF headers .
I login in fail safe mode, terminal, try to repair file system with fsch, also when I ifup network card, i see another invalid ELF headers error on another libraries, cmov/   .
i tried to apt-get remove install  gone-desktop, etc,  but nothing worked ,
any ideas or sugestions ??  also I renamed and put an old xorf.conf  ( I saw some thread about this error and open office ), but still not working .

regards
Eze

PS: if i put my livecd Ubuntu, and reinstall, i will lose all my system configurations ???

---

### Post by Stephen Howard on 2007-05-04
sounds like a dying harddisk maybe?

---

### Post by Stephen Howard on 2007-05-04
> PS: if i put my livecd Ubuntu, and reinstall, i will lose all my system configurations ???

Yes, you'll lose everything - that is unless you have /home on its own partition, in which case you'll be okay because you can tell the installation program not to format the partitions you want to keep.

If you don't have a separate partition for /home, then your only option is to backup your /home/ directory and restore it later.

---

### Post by egoldtech on 2007-05-05
hard drives looks ok, after many cheeck with Power mix tools, also im still using my windose partition,
I have my home on a separate partition, but i will miss ol settings, on extra software, apache, terminal services, etc .....
what kind of error is invalid ELF headers? what happens here? , why if if found invalid headers on for example
libgnome-2, after REMOVE and reinstall via apt-get, im still having this problems?

---

### Post by egoldtech on 2007-05-05
also I want to say, I cant find my backup.tar I made like 6 weeks ago .
I think I deleted a few days ago "to make some space" ....
je je I do not recomend do that folks .

---

### Post by Stephen Howard on 2007-05-05
hmm, have you compiled your own kernel?

Can you cut & paste a sample full error text?

---

