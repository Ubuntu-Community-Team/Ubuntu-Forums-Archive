---
title: "Problem starting"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Bardobrave on 2007-04-29
Hi to everyone.

I´ve tried to install the 7.04 from CD and I´ve found that every time I select any option, few seconds after start loading the kernel the screen powers off and complete system seems to hang. The most annoying matter are the Caps Lock and Scroll Lock leds, they start blinking... maybe they want to say me something...

I´m not sure if the problem could be of the video card, I´ve an ATI Radeon x800, but I´ve tried starting in video safe mode and the result was the same.

Any advice will be helpful.
Thank you all.

---

### Post by Metacarpal on 2007-04-29
Hm.  A video card problem wouldn't cause blinking LEDs on the keyboard.  Three quick questions to narrow down the list of suspects:

1. Is your computer running on an Intel processor, an AMD processor, or is it an Apple?

2. What is (a) the name of the .iso you downloaded, or (b, if you got your CD in the mail) the label on the CD you received?

3. How much RAM (memory) does your computer have - is it more than 256MB?

---

### Post by Bardobrave on 2007-04-30
AMD Athlon 3500+ processor.
2 Gb RAM memory.

I´ve downloaded the ISO for AMDx64 processors.

---

### Post by Metacarpal on 2007-04-30
So much for that theory.

Did you [check the md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso after you downloaded?  And when you start from the cd, did you "Check CD for Defects"?

---

### Post by Bardobrave on 2007-04-30
When I try to make the comprobation from the boot menu the problem repeats.

I haven´t made the md5 cheksum comprobation and I´m starting to think that the problem could be that I burned the CD at too high speed.

I´ll try with another CD burning it slower... and of course I´ll check de md5 integrity.

---

### Post by Bardobrave on 2007-04-30
Ok, it´s official, I´m in blank.

I´ve checked de md5 and it´s ok; I´ve also recorded again the .iso to a CD at X4 speed (slowest speed my burner allows) and I´m still getting the same problem.

Any advice to a newbie out of resources?

---

### Post by Metacarpal on 2007-04-30
I'm at a loss.  Sorry.  :( 
Maybe post a new thread with the title "Feisty install problems on AMD64" - that might get you help from someone with more specialized knowledge than mine.

---

### Post by blazercist on 2007-04-30
Ok, hit f6 ? I think its f6... anyway then it gives you the boot line, remove the part that says " splash quiet" hit enter.  It should work.

If that doesn't work then I dunno, capslock and all that is only supposed to blink with kernel lock.... I dunno I had the same problem, I can't remember what I did though... PS unless your system has 3592435689423 GB of ram then you don't need 64 bits anyway.

---

### Post by mejy on 2007-04-30
Have you tried running a memory test?  You'll probably have better luck with the i386 CD - it shouldn't be too much of a performance loss, and, particularly on what are effectively interim releases such as feisty, Ubuntu's tested more on it than any other platform.

---

### Post by StarFire039 on 2007-04-30
My computer did that, but was fixed when I plugged my monitor into a different output on the graphics card (it has two). If yours has two, try plugging it in the other one.

---

### Post by chickenjump on 2007-05-01
I had the same problem (AMD 3200 and a ATI X700).

Try this:

Download and burn alternate desktop CD.
Boot the CD.
press F4 to change resolution  to 1024 x 768 (color 16)
choose to install a commandline system. When it is done, log in and ...

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install x-window-system
sudo apt-get install gnome
sudo dpkg-reconfigure xserver-xorg (choose ati for your  x800, and set your resolution)
startx

It worked for me :)

---

### Post by Bardobrave on 2007-05-01
Ok, now it´s running.

I´ve tried the [quiet splashless] boot from F6 and it´s done.

From now I´ve a new fight to install it and configure all. An intrigant one for one windower like me.

Thank you all for your help.
I´ll post my advances.

---

