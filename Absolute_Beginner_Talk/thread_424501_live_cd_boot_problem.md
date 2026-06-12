---
title: "live cd boot problem"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-04-26
ok so I decided to convert a friend to linux and she has an old hp. It came preinstalled with windows xp home and I think it was manufactured somewhere around 2001, I am not sure of the hardware specs tho.
So anyways, I tried to boot both in normal and in safe graphics mode. Both get past the intro music but after that all I see is the brown background color and grey colors of the panels, cd rom light is still blinking but it stays that way. sometimes I get some gome error window sometimes I don't.

I thought it would be able to run ubuntu since it was able to run windows xp
should I try xubuntu or there is some other way?

---

### Post by Gmbrdilos on 2007-04-26
help anyone?

---

### Post by Gmbrdilos on 2007-04-26
please I need some help quick, anyone?

---

### Post by Midgetmunky13 on 2007-04-26
holy crap man be patient. as for your problem i cant really help you im kinda a noob. i have a problem myself. i dont know how to upgrade from dapper to fiesty! hope u find help

---

### Post by Skidpad on 2007-04-26
You need to look at the system specs - it may not be enough to run the cd - even if it does have 256mb of ram.  It still might be choking on it.   Alternate (text-based) cd perhaps?

From the website, here's the Ubuntu requirements:
System Requirements
Ubuntu is available for PC, 64-Bit and Mac architectures. CDs require at least 256 MB of RAM. Install requires at least 2 GB of disk space.

---

### Post by Gmbrdilos on 2007-04-27
ok I tried the alternate text based disc, it got past the kernel installation, but when it got to a screen saying select and install software, it got to 6% then jumped back to 2% then came back to 6 again and stopped the message under it says please wait, and was there for quite a while. I also tried the Xubuntu alternate cd, same thing happens, stuck at 6% of that screen.

Found out more about the computer, it's a celeron and has 174 mb of ram (weird, RAM comes in binary numbers usually)

do you think there is faulty hardware?

---

### Post by dude051 on 2007-04-28
You should run a few test on the system before the install first. First off, boot the CD and run the CD Test to check for errors, if fine go and run the Memory Test for about 30mins or more (the better). If no errors here your system should be fine to run everything, with exception to the LiveCD. The reason you need 256mb of ram to run the Live CD is that the main Ubuntu system contents are pre-loaded into the ram, which takes up a lot of space. 
Your going to have to run the text based installer there if you got 174mb. It's hard to say how you have 174mb of ram, but what it sounds like is the internal graphics are steeling ram. What I think is 128MB+64MB for a total of 192MB, but your internal graphics are sucking off 16MB (176MB). You might try looking up in the BIOS and see if theres a value set for your graphics to steel. It's the best explanation I can think of. 

Also, do not use Xubuntu, this is the server edition of Ubuntu, if you want an alternate install that is desktop based then use Kubuntu (KDE).

---

### Post by Gmbrdilos on 2007-04-28
I am not much of a fan of kubuntu, I tried xubuntu because I heard it was better for older computer, didn't know it's a server thing though. Thanks for the suggestion, I will try it on Monday.

---

