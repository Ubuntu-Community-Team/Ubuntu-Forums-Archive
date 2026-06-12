---
title: "Installation problem"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Sandesmus on 2006-06-13
So, on the advice of a few of my friends I decided to install Ubuntu on my PC. After downloading the ISO and putting it off for a few weeks I finally decided to install it. 

I burned the ISO to a disk, restarted my computer, selected "Start or install Ubuntu" from the menu of boot options, and waited for the installlation to begin. I ran into my problem when the installer got to "Preparing hardware drivers". After it got to that point, I got a repeating error message that said something along the lines of:

[stringofnumbers.stringofnumbers] eth0: (stringofnumbers) System Error occurred (0)

The error kept repeating, with the numbers in each field getting slightly higher each time. I tried booting with LiveCD, and the same thing happened. Also, an error check on the disk turned up nothing.

Any idea of what my problem might be?

---

### Post by drtvasudevan on 2006-06-13
i donno anything about the error msg but unless you post some specs of your pc too it will be little difficult for people to trouble shoot.
also if you put it off for a few weeks it is likely to be the beta version rather than the final release. dapper got released only inthe first week of this month.
btw is it dapper that you downloaded?
see so many missing details!
thanks
tv

---

### Post by Sandesmus on 2006-06-13
Yeah, I figured I might have to post some more details.

Anyhow, here's a set of specs for my computer:

CPU: Intel Celeron 2.7GHz
RAM: 1 GB
Video Card: Intel 828445G/GL/GE/PE/GV Graphics Controller
Motherboard: Some generic Intel board (Not sure exactly how to get more specs)
Modem: Motorola SB5101 SURFboard Cable Modem
Network Adapter: Intel PRO/100 VE

Oh, and I forgot to mention that I did check to make sure I had the latest version before I tried to install Ubuntu. So, I'm using Ubuntu 6.06. Sorry for being so vague.

If you need any more information just let me know.

---

### Post by u.b.u.n.t.u on 2006-06-13
When you begin to install ubuntu there should be an option to check the CD to make sure it is error free. That may be worth doing.

---

### Post by Sandesmus on 2006-06-13
Like I said in my first post, I tried the error check and it didn't find any. I just tried again to be sure, still nothing.

---

### Post by Sandlst on 2006-06-14
From the eth0 part in the error message you gave, I would guess it doesnt like your network card for some reason.....you could try removing the card, installing ubuntu, then re-enter the card and hope it plays nice.....Im not sure what else you could try short of buying a new network card, but go ahead try removing it to see if that is the problem.  Hopefully someone else has some ideas. Also, are you using the new "Desktop CD"?  If so, can you connect to the internet from there?

---

