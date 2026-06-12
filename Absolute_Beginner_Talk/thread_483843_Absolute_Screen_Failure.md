---
title: "Absolute Screen Failure"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by britishguitar on 2007-06-25
I'm running 7.04 on a Compaq Presario 5000, and everythings been going nicely since I installed about a week ago. Then today, out of the blue, I went to turn the machine on, and it sounds good, the monitor light changes to green... and that's it. Nothing else. I've read other threads about people who get to a boot screen at least, but I have absolutely nothing on my screen at ANY point. A barrage of keyboard combinations (Ctr + Alt + F#) does nothing. Neither does restarting the machine/monitor.

I've tested out the connections and they all seem sweet. If I pull the plug out of the tower a message saying "No Signal" comes up.

Any answers out there? Thanks.

---

### Post by swisscow on 2007-06-25
No particular solution springs to mind but you could help eliminate some of the possibilities by booting from the livecd - at least if you get a screen then you know it's not your hardware that's gone kaput.

---

### Post by britishguitar on 2007-06-25
Okay, tried to boot from Live CD and nothing happened. I'm confident that the monitor is still working, as it can detect when it's not plugged in, and I still can get the Contrast/Brightness Controls up.

Just remembered that the computer MIGHT have been last turned off while trying to boot in Safe Mode(or whatever the Linux equivelent is). Could that royally screwed something up?

---

### Post by Golyadkin on 2007-06-25
This seems more likely to be an issue with your hardware though, maybe a faulty powersupply or memory.

Does the computer beep when it starts? Do the fans start? Do you get the BIOS?

If not, try resetting the BIOS on the motherboard (with a jumper, or by removing the CMOS battery for a few seconds.)

---

### Post by britishguitar on 2007-06-25
> **Golyadkin said:**
> This seems more likely to be an issue with your hardware though, maybe a faulty powersupply or memory.

Does the computer beep when it starts? Do the fans start? Do you get the BIOS?

If not, try resetting the BIOS on the motherboard (with a jumper, or by removing the CMOS battery for a few seconds.)

Okay. The computer doesn't beep, it never has. The fan sounds like it is starting, and as I said, absolutely nothing is coming up on the screen. AT ALL.

Is there somewhere were I can get more detailed information on how to reset the BIOS?

Thanks for your help so far.

PS: What could have caused the hardware to go? It was working fine a few hours ago.

---

### Post by Golyadkin on 2007-06-25
I had the same with my laptop, the motherboard was fried due to overheating.

There are some other people with the same problem, for them clearing the CMOS battery doesn't work. 
[http://forums.majorgeeks.com/archive/index.php/t-31912.html](http://forums.majorgeeks.com/archive/index.php/t-31912.html)

It is just a simply round shiny battery, about 1cm in diameter, that is sitting on your motherboard. You can take it out and put it back in.

---

### Post by britishguitar on 2007-06-25
> **Golyadkin said:**
> I had the same with my laptop, the motherboard was fried due to overheating.

There are some other people with the same problem, for them clearing the CMOS battery doesn't work. 
[http://forums.majorgeeks.com/archive/index.php/t-31912.html](http://forums.majorgeeks.com/archive/index.php/t-31912.html)

It is just a simply round shiny battery, about 1cm in diameter, that is sitting on your motherboard. You can take it out and put it back in.


Hmmmmmm... I'm getting things on the screen, but I'm not sure if everything is good yet. I'll post back later.

---

### Post by britishguitar on 2007-06-25
YAY! It worked!

Thank you!

---

### Post by Golyadkin on 2007-06-25
You are welcome, it usually has to reinitialize after resetting the BIOS.

---

