---
title: "running lion in a virtual environment under kubuntu"
date: 2011-08-31
forum: Apple Hardware Users
---

### Post by benny rascal on 2011-08-31
I run multiple distros and my production one has been kubuntu for about 3 years. Current production is natty. I have vmplayer installed on one of my distros and virtualbox installed on natty.  My main PC is a core i7 3.20 GHz with 8 GB RAM and an ASUS 6850. The machine is fast and also surprisingly runs cool (cpu and mb about 30 degrees, NB 42 degrees). Today is the first day of spring in Australia so do expect those temperatures to rise in the coming months. 

That is my main environment. Now to my question.  In July i bought a Mac Mini, the 2.3 GHz i5 with 2 GB.  At first I thought I'd use it as a backup for my main PC using its boot manager and kubuntu.  Was also hoping to port a lot of my development across to it. Most things i write are in Python using Qt and use SQLite for my databases. Seems there shouldn't be many issues there. Found Python installed on it and then got into the Apple store and downloaded xcode. Also got Qt in with no problems.  What I was finding out in doing this is how relatively slow the Mac was.  Used Google and there were other users with similar problems and they were blaming Lion.  I'm not all that bothered about it as it is more like a toy to me, something I'd like to learn about but am not dependent on.  In doing development for the Mac I thought it would be faster to get it working under my fast PC and then just copy it across. Am not sure on the copyright side what I'm allowed to do dealing with running OS/X in virtualbox. Lion came pre-installed with no install DVD. This kind of suggested to me that I'd have to purchase another copy of it. BTW, when i mentioned relatively slow it was comparing kubuntu in a 3rd PC of mine which is a Pentium D (I have 13 PCs now but most are packed up waiting for their chance in case one of the main ones carks it). 

So any info on what I'm legally allowed to do would be useful.  I use virtualbox to run some old applications under XP and they fly. So am sure running OS/X using virtualbox will not have performance problems.  One option I have thought about is getting an earlier version of OS/X to do my development on my i7 and then port that across to the Mac.

benny

---

### Post by handy on 2011-08-31
Legally, OS X. is not allowed to be installed on non-Apple hardware. Using a VM doesn't create an escape route from the law.

---

### Post by benny rascal on 2011-08-31
Handy

Find that interesting as both virtualbox and vmware support OS/X and seems hard to believe people would be running OS/X under OS/X on a Mac.  Also, when I bought my Mac at the Apple store in Perth, I was told it is legal to run Linux and/or Windows on the Mac.  Seems then that Apple is saying you can use my hardware to run any OS but only run my OS on my hardware.  I can now see why this thing called a jailbreak exists for mobiles, etc.  Am wondering if what you say is true in all countries as copyrights here are different than in the States where Apple is based.  Mayhaps I've been using open source for too long.  Before I retired back in 2003, I worked as a developer at IBM.  We wrote software for IBM mainframes but any one could buy the software and use it on an Amdahl or other hardware that was competition to IBM.  That went back to the unbundling that IBM was forced to do back in the seventies, or was it the sixties.  Microsoft also had to unbundle their Internet Explorer from their OS more recently.  So I am really surprised if it is true that OS/X can only be legally run on Mac hardware.

It would seem that one could still buy OS/X and then install it under virtualbox without ever connecting it to the internet.  Why would they care about that? Being that I was being paid to develop software for most of my 43 years in computers before retirement (started on IBM EAM machines in 1960), I'm loath to 'break the law' in this area.  However, there must be some sort of realism in that if I pay for the software and already own their hardware.....

thanks for your comment

benny

---

### Post by handy on 2011-09-01
The Windows license allows you to install it on any hardware. MS are primarily a software house.

The Linux license is (as you know) open-source & not proprietary, it places no limitations regarding what hardware it is installed upon, to the point that the community of developers are continually expanding the list. :)

Apple, differ to the two above, in that it is primarily a hardware designer/manufacturer that happens to also produce operating systems & some software which enhances its products. Apple make their hardware more attractive (to most) with their software & cash in with smart marketing & value-added additions the likes of iTunes, & the increasing presence of the Apple Store in their systems. 

This gives Apple ample opportunity to make more profit & to (prior to Android) grow the market share of some of its hardware products.

So it is easy to see that Apple don't want their operating systems (in particular) being used on other hardware, as they don't make their money from software, most especially their operating systems; the current Lion version of OS X, sells for $31.99 !

Re. running OS X, via VM's on OS X;- it is not uncommon for people to run multiple virtual machines for various reasons. For testing, as servers... My ISP runs multiple virtual servers on Gentoo systems!! Who would of thought they'd use Gentoo as the base system (I guess if you have lots of identical hardware you build it right once, image it & then cast the image on the other empty servers).

Re. your rights of ownership;- You may own the hardware (you don't own the firmware on the chips though), you are only buying a license to use either Windows or OS X.

Both MS & Apple always retain the ownership rights. You should read the Apple EULA I think.

You will find a .pdf copy if scroll down this page a little:

[http://www.apple.com/legal/sla/](http://www.apple.com/legal/sla/)

---

