---
title: "few questions about seperate home partition"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2007-09-11
i have been viewing the videos at 
[http://screencasts.ubuntu.com/MoS2007](http://screencasts.ubuntu.com/MoS2007)

and when he show how to do a install he showed how to make a separate home partition. what got my attention is how  your settings are saved when you do a upgrade?
a few questions before i get my hopes up 
      would i be able to ( in the future) say just download the gusty iso and install it and what would i have to say to it on install so it would not mess up my home partition and be able to use it ?

   would there be any conflict with the versions/level of the files in home?

this would be on a dedicated Ubuntu computer

this looks like the way to go in the future so i am planning now and just can't imagine a free ride of saving all the settings pics andtprograms f and getting the latest Ubuntu without any troubles?

comments please of advantage and disadvantage of doing this?

thanks 

ps think that site should be penned ( sticky) at the top as some good info on doing things with Ubuntu 

mitch

---

### Post by llamakc on 2007-09-11
It works wonderfully. I've been doing it this way since Warty. I never have to reload music, pics, and other files. They're all right there.

When you do the install of Gutsy, you tell the partitioner NOT to format the partition where /home is, and to mount that partition to /home and to 'leave existing data'.

---

### Post by reckless2k2 on 2007-09-11
yeah i use this separate home partition as well across multi boot distros. works very well. if you have to do a reinstall or such, it is a saver.

---

### Post by Paul133 on 2007-09-11
What you'll do is just format the / partition and keep the /home partition. Of course, you could also upgrade to Gutsy from Feisty without formtting anything.

---

### Post by the.phantom on 2007-09-11
> **llamakc said:**
> It works wonderfully. I've been doing it this way since Warty. I never have to reload music, pics, and other files. They're all right there.

When you do the install of Gutsy, you tell the partitioner NOT to format the partition where /home is, and to mount that partition to /home and to 'leave existing data'.


when in the partition does it give that option?

i have done full install and dual boot and don't remember anything?

( ya i wanna make sure i get it right when i do it for G !)

---

