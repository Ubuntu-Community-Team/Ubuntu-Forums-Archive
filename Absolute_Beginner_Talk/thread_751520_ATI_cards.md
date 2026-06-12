---
title: "ATI cards"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by dohboy13 on 2008-04-10
i have an ATI radeon X1300 video card that i installed a month ago, and i used to have ubuntu on my computer before that...but...i've tried the live cd and nothing comes up on the screen and i was reading that ATI cards aren't that well supported on ubuntu yet

so, could someone tell me how to get this working?

---

### Post by herbster on 2008-04-10
Did you try the second option, for safe graphics mode (in the LiveCD menu)?

---

### Post by dohboy13 on 2008-04-10
no i didn't, but would i have to start in safe-mode everytime i start ubuntu?

or would i have to find linux drivers for my card of ATI's website or somewhere?

---

### Post by Crafty Kisses on 2008-04-10
> **dohboy13 said:**
> i have an ATI radeon X1300 video card that i installed a month ago, and i used to have ubuntu on my computer before that...but...i've tried the live cd and nothing comes up on the screen and i was reading that ATI cards aren't that well supported on ubuntu yet

so, could someone tell me how to get this working?

What are your system specs?

---

### Post by Rocket2DMn on 2008-04-10
Not all cards work on the LiveCD, so you should either use the Safe Graphics mode, or download the alternate install cd from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate disc.  It uses a text based installer, but is very easy to use, and you will have a normal boot afterward.  Once you install and log in, you can install the restricted ATI drivers for your card.

---

### Post by Helios1276 on 2008-04-10
I have a x1400 and I used Envy, which for me was an amazingly simple fix!! :popcorn:

---

### Post by dohboy13 on 2008-04-10
thanks, i'll try the other cd, and this "envy" thing,(i just googled it :P) and i'll see if it works

---

### Post by Helios1276 on 2008-04-10
you can get Envy in the synaptic package manager = System- Admin-Synaptic Package Manager. Just hit SEARCH "ENVY". When you download it , it should be in your system tools under apps. VERY easy to use . good luck mate :guitar:

---

### Post by herbster on 2008-04-10
You're basically using the safe graphics mode so you can at least get an X server (GUI) going, install the system and all that, then you can install the driver afterward.

---

### Post by dohboy13 on 2008-04-11
alright, thanks alot you guys, all try that tonight, i'll let you know if it works :P

---

### Post by frogotronic on 2008-04-11
I use an HP6910p laptop with an ATIx2300 RADEON card.  I've installed the proprietary driver and no problems at all.

Let us know is you have problems.

- CH

---

### Post by bm13084 on 2008-04-11
my xpress 1100 works fine using the restricted drivers, but compiz wont run....

---

### Post by captain_conrad on 2008-04-11
how do i figure out what model ATI card I have? my laptop has a very nice ati sticker on it and it says radeon HD 2400 XT. Now is that the model number? im confused out of my brains and im totally completely new to ubuntu, i also have absolutely NO clue how to work these forums but I can see that they are very valuable, so the first thing I want to do is figure out how to use the forums, then I want to find out what ATI card I have, and then I want to get my desktop cube working because I have rummaged through lots of these forums and found nothing anywhere near comprehensible, so i need basic basic basic english. by the way am I typing these questions in the right place? im so lost. please help.
PS ubuntu linux rocks, i cant even do anything on it yet, i just stare at the screen sometimes! it just feels SO awesome saying no to the worldwide windows domination!
hahaha thank u

---

### Post by stchman on 2008-04-11
> **dohboy13 said:**
> no i didn't, but would i have to start in safe-mode everytime i start ubuntu?

or would i have to find linux drivers for my card of ATI's website or somewhere?

Safe graphics mode uses a generic vesa driver.  Once Ubuntu is installed use Envy to install the ATI drivers.  Envy will modify your xorg.conf to use the fglrx driver.

---

### Post by herbster on 2008-04-11
captain_conrad, go to the Beginners' forum and click Make New Post. Be clear and specific with what you need help with.

bm13084, You are probably not running XGL?

---

### Post by bm13084 on 2008-04-11
im running the restricted drivers that automatically popped up in ubuntu.

not the same?

---

### Post by dohboy13 on 2008-04-11
right well it did work, but i couldn't get any games working, and my lights filckered when i  tryed to start warcraft 3, so i took it off, and i'll stay with windows till a full release of 8.04

thank you all for your help

---

