---
title: "HELP! My server is down!"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by handyguy33 on 2007-05-09
Hi all,

We've been running Ubuntu Server for about 7 months now, with no real problems to speak of. Today, we pulled it out to setup a RAID array. Well, somewhere between unplugging it and plugging it back in, it got messed up. Everything appears to be working, except for one little detail; no video display! This is an Asus MoBo with no history of hardware problems. We haven't even tried to install the SATA drives yet. The boot, when  we discovered the problem, was just a routine check before we actually started to work on it. I know right off the bat, that you will want particulars, so here we go:

Asus P4P 800 Deluxe Motherboard
Nvidia G-force 440 AGP Video card
Ubuntu Server 6.06 OS

We've already checked connections, tried alternate video cards and monitors. Frankly, I'm stumped. It's very close to the end of the work day at the time of this post, so I probably won't respond to anything until tomorrow.

Please help, I really need to get this fixed this week.

---

### Post by Wicca on 2007-05-09
When does the video display stop working? Can you see - and enter - the BIOS setup?
If not, it's definitely a hardware issue. Some beep(s) will sound when you power up the machine; these will give you a clue about what's wrong. See the manual of the mobo.

If you can however see the BIOS setup menu and the video stops working after the initial boot, i haven't got a clue.

---

### Post by handyguy33 on 2007-05-09
We can't get BIOS. The only indications that the MoBo isn't toast are the physical indicators (LED's and such) on the board itself. No beeps to indicate a problem with the CPU or the power supply.

---

### Post by compmodder26 on 2007-05-09
If you can't even see the BIOS then I'd have to say it is a hardware problem.

---

### Post by Wicca on 2007-05-09
I agree with compmodder26: it is hardware failure. Since you did try another GPU and monitor (cable as well?) it must be (a part of) the mobo. 
Looks bad. If you have a spare mobo battery lying around, try it. You'll never know.

edit:
Instead of a beep, the power light might flash in a certain pattern. I remember years ago a certain mobo did that to indicate a hardware problem.

---

### Post by kerry_s on 2007-05-09
oh, oh, static discharge? 
Did you ground yourself before touching the motherboard?

---

### Post by handyguy33 on 2007-05-10
Thanks for all the input. It was the battery, whew. I have to say that the support here is great. I was really stumped.

---

