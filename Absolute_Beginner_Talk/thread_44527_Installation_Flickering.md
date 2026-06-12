---
title: "Installation Flickering"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by Moosferatu on 2005-06-26
I just downloaded the Ubuntu install CD and tried to install it, but I ran into a problem.  After I hit enter for the first time and got to the first screen where I'm supposed to select the language the screen starts to flicker or loop or something really quickly making it unreadable.  I figure it might be a problem with the video card or something, but I couldn't find any help with it online.  Does anyone have any idea what the problem is and how to fix it?

My specs:
Dell Inspiron 6000
Pentium M 1.86GHz
ATI Mobility Radeon X300 128MB
512MB DDR2 SDRAM

Would anything else be useful?  I tried updating my drivers, but they're current.

---

### Post by Sionide on 2005-06-26
I would assume from that, it's trying to display the installation screens at too high a resolution but I thought they displayed at 640x480 anyway so I'm not sure how to fix it - but that's what it sounds like. Can't imagine why it's happening...

Have you tried using a different monitor?

---

### Post by Moosferatu on 2005-06-27
Thanks!  That monitor suggestion works.  Weird.

---

### Post by kaiserzoze on 2005-06-27
I had the same problem but I change in BIOS (F2 kay at start up) the LCD expansion to off, and I installed in a small window. All was ok

N.B. BIOS A06 do not fix this problem.

---

### Post by Beawulf on 2005-09-19
I had this exact problem trying to install it last night.

I tried another monitor but that didnt fix the problem, however they are both the same type of monitor. Will try to get my hands on another.

the suggestion for changing the bios setting, I assume that only relates to people using LCD screans?

My system is:
AMD 2800+
asus A7-8X E deluxe
1gig DDR
2x80Gig western digital
geforce fx5200 128MB
monitors: compaq v75 17"

The system runs fine with other operating systems

---

### Post by kaiserzoze on 2005-09-20
Yes, 
turning LCD expansion off is for a inspiron 6000 Laptop
.

Can you try with another Video Card?

Also try to pass the parameter vsync=60 to the Intalation kernel's image, may be it's a over vertical syncronism problem.

---

