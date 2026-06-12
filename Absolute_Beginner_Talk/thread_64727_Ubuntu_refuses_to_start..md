---
title: "Ubuntu refuses to start."
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by vordrax on 2005-09-11
**Edit: Problem solved by poofyhairguy!**

Alright, I installed Ubuntu 5.10 earlier. The installation is fairly straightforward, so hopefully I didn't manage to screw that up!

Everything seems to be going well, until the time comes to actually log into my user account. I type in my name, password, log in- nothing. The screen is just dark orange. I left it alone for about 5 minutes, and nothing happened. I restarted my PC, and tried again.

I figured that it might be a driver problem, so I tried to change the session to "Failsafe Terminal"- nothing happens. I click on Sessions, Failsafe Terminal, and my PC freezes. Well, I can move the mouse, but I cannot affect anything at all. The Session menu just sits there, frozen.

I tried redownloading Ubuntu 5.10 and burning it to a different CD-rom, deleted the old partitions and reinstalled. Same thing happened.

One of the messages coming up at the start comes out as "Failed"- it scrolls pretty quickly for me, but it says "Console Font" or something to that effect.

My hardware configuration is thus:

Athlon XP 2800+ (Barton)
768 megs of RAM PC2700 (the 512 stick is damaged slightly, it's getting replaced soon)
nVidia Geforce 6800 (factory overclocked by BFG)
A7N8X-X motherboard
80 gig harddrive, a 5.5 gig partition for Ubuntu, the rest for Windows and a storage partition.

Is it a problem with the 5.10 preview edition? Should I just get 5.04? Or is there something wrong with my PC that might be causing the problem?

I'll give anymore information as needed!

(PS- I apologize if this has been answered before, I wasn't sure exactly what I should have Searched for.)

---

### Post by aysiu on 2005-09-11
It's kind of hard to know what exactly's wrong, but...

1. If this is your first time using Ubuntu, I'd recommend going for 5.04 instead of 5.10. 5.10 is "beta" for a reason--it's not reliably stable yet.

2. Did you do a checksum on your ISO image before burning it?

3. Did you burn the ISO at a slow speed (2x or 4x)?

---

### Post by vordrax on 2005-09-11
[QUOTE=aysiu]It's kind of hard to know what exactly's wrong, but...

1. If this is your first time using Ubuntu, I'd recommend going for 5.04 instead of 5.10. 5.10 is "beta" for a reason--it's not reliably stable yet.[/quote]

I'm probably going to have to do that, I was just reaching out to the community to see if they had seen this problem before I waste another CD (and I'm worried it might be Ubuntu not liking my PC, rather than just the version.)

> 2. Did you do a checksum on your ISO image before burning it?

No I didn't (should have though) but since I downloaded two copies of the ISO on two different occasions, and managed to come across the same error twice, I don't think it's a problem with the ISO itself (unless the iso on Ubuntu's main mirror is damaged.)

> 3. Did you burn the ISO at a slow speed (2x or 4x)?

The first time I burned at 16x, the second time at 8x.

---

### Post by vordrax on 2005-09-12
Bump. I installed Ubuntu 5.04 this time, and it has the exact same issue.

I think it has a problem with my nVidia card but I'm not absolutely sure. Anyone have ANY idea?

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=vordrax] Should I just get 5.04? Or is there something wrong with my PC that might be causing the problem?
[/QUOTE]

Nvidia cards are the best for Ubuntu. I personally had x problems with Breezy and had to nerd my way through it. want to try?


When the computing it booting keep hitting esc to see the grub screen. The first option should be like "Linux....." pick the second one that talks about a recovery mode. Then when you hit the prompt, put in this command:

> dpkg-reconfigure xserver-xorg

Answer its questions. when you are done type

> exit

If that doesn't work install Hoary please.

---

### Post by vordrax on 2005-09-13
**poofyhairguy**, thank you very much! I am posting this on my now-working Ubuntu :) It looks great! I thought it might be the video card drivers, but you solved my problem perfectly!

---

### Post by poofyhairguy on 2005-09-13
[QUOTE=vordrax]**poofyhairguy**, thank you very much! I am posting this on my now-working Ubuntu :) It looks great! I thought it might be the video card drivers, but you solved my problem perfectly![/QUOTE]

Thats what I am here for. No problem.

---

