---
title: "LiveCD Freezes every time"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by SamirNaninanajeb on 2007-05-12
So a friend told me about Ubuntu and got me interested in linux and I really want to try it out.  I have 1 gig of ram and 80 gb harddrive an amd athlon64 3200+ and an ATI allinwonder 9800 video card.  I first downloaded the 7.04 64bit iso file.  I verified it with md5summer and everything went fine.  When I tried to boot from the cd, I chose Run or Install Ubuntu and after hearing the intro sound my mouse stopped working and nothing happened.  I tried running in safe graphics mode and the same thing happened.  Someone recommended that I try the 32bit version so I downloaded that ISO and I STILL HAVE THE SAME EXACT PROBLEM!!!...  

can anyone help?

---

### Post by taurus on 2007-05-12
Do you just want to try it out as in running it from a LiveCD so do you want to try it out as in installing it on your machine?

Try the 32bit alternate CD if you want to install it on your machine.

---

### Post by SamirNaninanajeb on 2007-05-12
I'd rather not install it because I dont know much about it, I've never used it and I need windows for school.

---

### Post by nickpaton on 2007-05-12
Also on the first choice menu, use the CD check option to make sure you have no damaged programs.

Also burn the CD VERY slowly (I do it at around x5) and use a good quality CD-R, not a rewriteable CD-RW.

I also agree with Taurus (wouldn't dare disagree LOL) on the alternative CD option which should work but you will need to make sure of the above things as well.

BTW welcome to the forums and ubuntu

---

### Post by SamirNaninanajeb on 2007-05-12
I did the CD check and it works fine.  Ive heard there are problems with ATI video cards... Could this be what I am experiencing... is there a way around it?

---

### Post by nickpaton on 2007-05-12
I'm running 7.04 on a 64bit laptop with an ATI card and didn't have any problems.

What is the make model of your PC /laptop?

Are you trying to dual boot, and if so what is the size of the partition.

Also what size swap have you made, it should be 2 x RAM size.

---

### Post by SamirNaninanajeb on 2007-05-12
I dont want to actually install Ubuntu I just want to run it off the cd... i have no partitions.  maybe that is my problem.  My computer is a custom built pc from ibuypower.com.


and swap?  i have no idea

---

### Post by L Campbell on 2007-05-12
> **SamirNaninanajeb said:**
> So a friend told me about Ubuntu and got me interested in linux and I really want to try it out.  I have 1 gig of ram and 80 gb harddrive an amd athlon64 3200+ and an ATI allinwonder 9800 video card.  I first downloaded the 7.04 64bit iso file.  I verified it with md5summer and everything went fine.  When I tried to boot from the cd, I chose Run or Install Ubuntu and after hearing the intro sound my mouse stopped working and nothing happened.  I tried running in safe graphics mode and the same thing happened.  Someone recommended that I try the 32bit version so I downloaded that ISO and I STILL HAVE THE SAME EXACT PROBLEM!!!...  

can anyone help?

I, too, have a similar problem with my HP Pavilion 753n machine (Pent 4, 2.53 GHz. 1GB RAM, 80GB Hard Drive)

I'm using the 'official' (from Ubuntu) Live CD and I get the same 'freeze up' after choosing 'Run or Install Ubuntu'.

Also, using a Live DVD produces the same result.  I'm sure the problem is in my machine, not the Live CD/DVD but I have NO idea what to look for and would really appreciate some assistance here.

---

### Post by nickpaton on 2007-05-12
OK - Why not simply install ubuntu and see how you get on.

However you don't seem to be familiar with some aspects of installing Ubuntu, so may I suggest you read some of the articles from the[ Psychocats]("http://www.psychocats.net/ubuntu/") site - very readable and full of good down to earth sense!

Within Psychocats, if nothing else read [this article]("http://www.psychocats.net/ubuntu/installing") on how to install ubuntu from a CD. 
It contains screen prints of each of the major parts of the installation procedure and the part on partitioning is particularly useful.

---

### Post by nickpaton on 2007-05-12
@ L Cambell - I too have an HP laptop.

I had a problem in Edgy when installing that the lappy overheated and shutdown before I could fully install the distro.

What I did was to go into the BIOS and enable the fan to be on all the time when run on AC.  I'm not sure if Pavillions have a similar BIOS but it could be worth trying.

Also what I tend to do is at the initial selection screen to select F6 other options and to type in:

```
noapic nolapic
```

This will be added to the line of code which appears when F6 is pressed.

This used to be a Breezy, Dapper fix for installing on many PC's.  No harm in trying and could fix the problem.

---

### Post by nickpaton on 2007-05-12
For both of you - 

At the first choice menu on the CD, it may be worth checking your memory is OK by running memtest86.  It's a fairly basic memory tester but will show any major chip failures.

Also I've read elsewhere that someone with such a problem reset their BIOS to the default settings and this solved the problem.

---

### Post by L Campbell on 2007-05-12
> **nickpaton said:**
> @ L Cambell - I too have an HP laptop.

I had a problem in Edgy when installing that the lappy overheated and shutdown before I could fully install the distro.

What I did was to go into the BIOS and enable the fan to be on all the time when run on AC.  I'm not sure if Pavillions have a similar BIOS but it could be worth trying.

Hi, thanks for your interest.

Sorry I didn't explain more clearly but my HP is a PC, not a laptop.

I did, however, take your suggestion and checked my BIOS (CD, Hard Drive, Removable, LAN) but didn't see any mention of the fan.

Kind regards.

---

### Post by nickpaton on 2007-05-12
Apologies Lewis my stupid!

There won't be any mention of fans on a desktop BIOS!

Try the noapic additon as above (don't bother with nolapic).

For more information on this have a look at [this]("http://ubuntuforums.org/showthread.php?t=228499").

---

### Post by nickpaton on 2007-05-12
A quick troll through the forums for people having this problem does suggests using Alternative CD, and in most cases seems to load a lot better.

At the end of the day it may the only solution when all else has failed.

---

### Post by L Campbell on 2007-05-12
> **nickpaton said:**
> A quick troll through the forums for people having this problem does suggests using Alternative CD, and in most cases seems to load a lot better.

At the end of the day it may the only solution when all else has failed.

Thanks for this suggestion.

Do you know where I might be able to download this Alternative CD?

My searches didn't find it.

Kind regards.

---

### Post by nickpaton on 2007-05-13
> **L Campbell said:**
> Thanks for this suggestion.

Do you know where I might be able to download this Alternative CD?

My searches didn't find it.

Kind regards.

First of all go to[ this]("http://www.ubuntu.com/getubuntu/download") page, and scroll down to the very bottom to where it says "[COLOR="Red"]_complete list of download locations_[/COLOR]".

Click and on the new page scroll to your country mirror.  I am assuming you are from USA and in this case pick gigenet.

The new page will list all the available distros so click on 7.04 for that mirror.

For 7.04 select  [this]("http://mirrors.gigenet.com/ubuntu/7.04/").

Then scroll down to Alternative Install CD and select "PC (Intel x86) alternate install CD".
Click and download as normal.

HTH

Nick

---

### Post by L Campbell on 2007-05-13
> **nickpaton said:**
> First of all go to[ this]("http://www.ubuntu.com/getubuntu/download") page, and scroll down to the very bottom to where it says "[COLOR="Red"]_complete list of download locations_[/COLOR]".

Click and on the new page scroll to your country mirror.  I am assuming you are from USA and in this case pick gigenet.

The new page will list all the available distros so click on 7.04 for that mirror.

For 7.04 select  [this]("http://mirrors.gigenet.com/ubuntu/7.04/").

Then scroll down to Alternative Install CD and select "PC (Intel x86) alternate install CD".
Click and download as normal.

HTH

Nick


Thank you very much, Nick, this is perfect

I had got about half way there by myself but it was buried so deeply that I thought I was in the wrong area.

Kind regards.

---

