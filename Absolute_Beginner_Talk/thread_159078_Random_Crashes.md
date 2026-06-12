---
title: "Random Crashes"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-04-12
I have Ubuntu on a 1.8 GHz Sempron with 512 KB RAM, onboard S3 graphics.  Ubuntu seems to crash randomlly, resulting in everything frozen and a screen composed of vertical grey lines.  I call it the GSOD.  This happens really randomlly, whether doing something memory intensive or playing solitaire.  It happens often, too (at least twice per day).  I haven't tested the RAM out from the GRUB menu yet, but I doubt that is the problem as I had no problems with the RAM using Windows.  Any ideas about what is causing this, or how to figure out what is causing it?

---

### Post by Sef on 2006-04-12
Since Windows works fine, I would say it is the ubuntu.   Have updated it lately?  When did this start?  After you installed any software?

---

### Post by BarFly on 2006-04-12
Ubuntu is up to date.  I installed automatix, samba, Firefox 1.5, Wine, digiKam, and some games from the add applications menu, and codecs.  I just looked at the system monitor and nothing is really using any memory.  I did notice I can disable a bunch of stuff that launches upon start that I don't use in the System-Administration-Sevices tab.  Maybe something is launching in the background periodically that demamds a ton of memory.

---

### Post by Mustard on 2006-04-12
I would look through your logs in the /var/log/ folder to see if you can see any errors that might relate to the crash.

---

### Post by confused57 on 2006-04-12
It could be your integrated graphics.  I had a similar problem using a Chaintech Volari graphics card($10 after rebate) in Windows XP.  Installed a XFX Nvidia 5500 graphics card and haven't had any problems.  May or may not be related to your problem.  Linux wouldn't even run on the Volari graphics card.

---

### Post by BarFly on 2006-04-12
Mustard, I looked at the logs.  Everything looked pretty good to me.  Of course, I did not understand any of what I was looking at.

Confused57.  Yeah, that would make sense.  There is not a linux driver for Via Unichrome.  Whatever Ubuntu defaulted to (VESA?) I guess only works somewhat.  I will look into a cheap graphics card.

---

### Post by Marcboy on 2006-05-05
This is the exact same problem im having. Well nearly, i get green lines not grey, but its close enough. But im using a nvidia graphics card so i dont think thats the problem. And it doesnt seem to be due to memory intensive programs as you said. Did you ever find a solution to this?

---

### Post by Jason_25 on 2006-05-05
Weird lines with nvidia almost always mean you are using the "nv" driver with a newer nvidia card.

---

### Post by Marcboy on 2006-05-05
i wouldn't say its a newer card, geforce 4 mx (i think)

---

