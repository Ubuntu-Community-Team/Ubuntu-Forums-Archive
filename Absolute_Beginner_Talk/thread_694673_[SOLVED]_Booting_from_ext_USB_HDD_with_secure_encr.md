---
title: "[SOLVED] Booting from ext USB HDD with secure encrypted internal HDD"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by mistergo on 2008-02-12
Hi folks,
I have one (theoretical) question regarding booting Ubuntu 7.10 from my external USB HDD plugged in "work-office" laptop HP Compaq nc6320.

Yesterday I have succesfully installed Gutsy on external Prestigion USB HDD 40 GB. The whole instalation I went through was without internal HDD (I had took it from laptop first). 

Why? It is laptop of my employer and unfortunately I had previously some mess with it (i have one official entry :)) so i wanted to be sure that nothing goes wrong ...
Internal HDD has Safeboot program install on it ([www.safeboot.com](www.safeboot.com)) which, if I undestand right, takes care of encrypting all data and you have to first log right after BIOS Boot Dialog Box in to boot Win XP.

Yesterday, after installation of Gutsy I turned off laptop and plug internal HDD back in. BIOS is set correctly to boot first CD, USB HDD, HDD, ... but when I choosed from dialog box USB HDD it started booting just for a while (couple of lines of text) and then stopped.

Yesterday I did not care and I unplugged intenal HDD and continued with enjoying my brand new Gutsy :) and also I can take any risk too ... but I can imagine that after a while it can be boring every day to plug/unplug internal HDD ... :(

I can post later error (i think it was there some on screen) I have got after this booting (later evening when I am back at home from work).

So after long introduction, I would love to hear that someone has/had similiar problem (no offence!) and luckily has solved it. Or what could happen anyway ...? 

One hint at the end of this story ... when I have been installing Gutsy I have formatted whole USB HDD (recognized as /dev/sda1) and I have left all preferences without touching (i.e. boot (hd0)).
Some details > Bios version 2.00 C3 + F.09 - 09/15/2006, dual core Intel T5600 (1,83 Ghz), multiboot enables :)

Thanx in advance for you effort!!
MisterGo

p.s. if any solution is at least a little risky i am not going for it for known reason posted above :) ... sorry

---

### Post by smartboyathome on 2008-02-12
I sometimes have a similar problem with my external hard drive. It takes ~10 minutes to go from grub to gdm on a cold start. I think it may be doing the same to you. Try waiting 10 minutes to see if it continues.

Also, what is the error you get?

---

### Post by mistergo on 2008-02-12
you will never believe me ;) ... i came from work earlier than i was planned and did something which hanged on my mind ... I put LIVE CD in, boot and choose from menu "Boot from first harddisk" and now i am posting this reply as I had wished yesterday before started installation at all ...

so ... hanging 10 minutes it's not my case ... but probably you could be right, i did not have  so much patient ... and other problem is solved too because Gutsy do not see my internal HDD which was very important for me not to mess with those data ...

And because of above mentioned new details I can't copy here any error ...

and feel quite stupid, but as i said, i wanted to be sure!

i am closing this post but thank you for quick answer!!!

MisterGo

---

