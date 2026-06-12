---
title: "Feisty install problems"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Evegan on 2007-06-08
OK, I know that double posting isn't cool but I posted this in the Installation section but I haven't gotten as much help as I would like. 

After running Hoary for a year or two I decided to do a clean install of Feisty. I burned a CD but also ordered one just to have a back-up. Well, a few days ago it came in the mail and I fired it up. Once I get to Step 4, Partitions, there are several options. 

#1 - Guided and resize which allows you to choose how much disk space to use for Feisty.
#2 - Guided and use the whole disk
#3 - Manual

First, I chose #1 but it kept telling me there was no root file directory system and I couldn't move on. Then, I went back and chose #2 and I was able to move on and install the system. Once it finished the install the info/status box just went away and I was left with the Live CD screen. OK, so I reboot the system and get a Grub Error 15 right away and the computer wouldn't go any further than that. Following the instructions of some helpful folks in the Install section, I tried the whole manual mounting procedure. Unfortunately that has not solved my problem.

Someone suggested I get the Super Grub Boot disk and try that, the only problem is I can't burn a CD while I'm running the Live CD. So I'm going to download and burn it at work today and try that tonight. My question about the grub CD is, when do I put that in? Before I boot the system? If so, will that load up Feisty or some other menu? Once I get it up, how do I figure out what my problem is?

Again, sorry for the double post in two different forums, but I'm grasping at straws and just need some help.

Thanks

Evan

---

### Post by lamalex on 2007-06-08
Do the install again and do manual partitioning and make sure it's got a mount point of /. I've had that problem before where it doesn't assign a mount point to my new intall.

---

### Post by dptxp on 2007-06-08
You wantdual boot ? Can you tell about your partitions ?
Manual partitioning may be best.

---

### Post by Evegan on 2007-06-08
I'll try the install again with manual. What should it look like though? I'm a noob to this so detailed instructions are best. 

I don't want dual boot, just Ubuntu.

Thanks

Evan

---

### Post by antoz on 2007-06-08
[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)
The above link explains grub errors, I looked at your other post "confused57" helped me a great deal with my install (I had lots of problems Boot, grub and login) but managed to get it going by following his instructions. Sorry can't help you any further myself, good luck, A.
You could post a screenshot of your partition table (use Gparted on the live cd)

---

### Post by Evegan on 2007-06-08
I just downloaded and burned a copy of the Super Grub Boot disk, hopefully when I get home this evening that will make it work.

My question is, obviously there is a problem somewhere. But how do I know which file is missing? On boot, it just says Error 15 and no other info. 

Also, with the grub disk, do I pop that in before I boot up the system? 

Evan

---

