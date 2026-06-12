---
title: "About to install Ubuntu 6.06 on my system just a few questions"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by mattgaunt on 2006-10-13
Hi every1

Im goin to install Ubuntu on my computer as soon as i get a second hard drive and i plan on dual booting with windows XP and ubuntu, but i have a few questions

Will Ubuntu install the software that i need to give me the choice of which OS to load during the boot up??

Also i have an ATI Sapphire Radeon9600XT graphics card, now ive been told by people that ATI and linux arent the easiest of things to sort out and when ever ive looked at threads for this before i havent understood a thing ](*,) so just wondering if any1 could explain what people are going on about when they tlk about setting up 3D graphics

Thanks to every1 for any help what so ever :KS 

Matt

---

### Post by pay on 2006-10-13
Welcome to Ubuntu and Linux.:) 

> Will Ubuntu install the software that i need to give me the choice of which OS to load during the boot up??Yes. The software is called grub and it automatically setup for you. Aslong as you don't have too obscure of a setup ie more than linux and windows.

With the Ati you have the choice of radeon drivers of fglrx driver. Radeon are opensource and fglrx are supported by ati. The main problem is Ati don't really support as Linux users as much as we want them too. The windows drivers are faster than the linux drivers.

---

### Post by Foudre on 2006-10-13
alrighty then, as for dual booting, i have both xp and kubuntu on the same hard drive, no issues with "making me choose", now i had some troubles with my graphics untill i found this [http://tazforum.thetazzone.com/viewtopic.php?t=2189]("http://tazforum.thetazzone.com/viewtopic.php?t=2189")
its a post about setting up "eye candy" called compiz, but it goes over how to set up the graphics drivers, DON'T TRY TO INSTALL THEM USING ATI'S WAY "it doens't work.." i tried ATI's "right way" i tried my way, both failed, but following the instructions on the post that linked to (different forum) i have full resolution, and and frame rate, couldn't install compiz still, (not related to my graphics though) but ya if you want to set your ati card just follow them , and for dual booting, during the install after a few choices, it sets up the grub loader by itself (for dual booting)

---

### Post by Foudre on 2006-10-13
lol i was doign something while typing so it took a awhile, but this dude answered right before me saying something similiar

---

### Post by CarpKing on 2006-10-13
Have you tried the LiveCD?  Did it work?  If yes, you'll probably have an easier time with ATI than I did.  If you do happen to be spit out into a black screen, follow the guide in my sig (seems to be the same basic thing as the other link posted) to install the proprietary ATI driver and everything will work quite nicely.  So even if all seems lost, it probably isn't.  You probably won't have any significant problems though; most people seem not to.

---

### Post by pay on 2006-10-13
You would probably be better off using the 2nd method "Using the drivers from ati.com" as then you will get the latest drivers. The drivers in the repositories are quite old. (atleast last I checked they were old)

---

### Post by Foudre on 2006-10-13
they may be old, but the ones from ati didn' agree with my computer too well, so i just go with what works for me, i can only recomend what i know to work, and the ones from ati  didn't do me too well

---

### Post by redDEADresolve on 2006-10-13
use this it will work

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by weird_c00kie on 2006-10-13
i installed ubuntu for the first time last week.
after being forced to reinstall it twice because the visual interface managed to corrupt itself somehow, i decided to try fedora core instead

fedora didn't work. it screwed up my GRUB, whatever that is, so i can't boot into my windows drive anymore

my suggestion? if you install ubuntu and it works, don't try anything else... minimises the risk of you running into the same pile of crap i find myself in now :p

---

### Post by igknighted on 2006-10-13
> **mattgaunt said:**
> Hi every1

Im goin to install Ubuntu on my computer as soon as i get a second hard drive and i plan on dual booting with windows XP and ubuntu, but i have a few questions

Will Ubuntu install the software that i need to give me the choice of which OS to load during the boot up??

Also i have an ATI Sapphire Radeon9600XT graphics card, now ive been told by people that ATI and linux arent the easiest of things to sort out and when ever ive looked at threads for this before i havent understood a thing ](*,) so just wondering if any1 could explain what people are going on about when they tlk about setting up 3D graphics

Thanks to every1 for any help what so ever :KS 

Matt

I have an ATI card, and the live CD for dapper wont boot (edgy does, however, so it's a promising sign).  Here's what I do:

1) Install via the alternate install CD.  It isn't as pretty, but it works.

2) When you boot for the first time, choose 'Single User Mode'.  This will take you to a text terminal (ie looks like dos), just for this boot.

3) type the following commands, one after the other(let them finish first):

```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

after these are all done type reboot and the system will reboot, let it boot normally and it should work like a charm from there

---

### Post by mattgaunt on 2006-10-13
thanks so much for all the help guys, im sure ill get it all up and running:rolleyes:

---

