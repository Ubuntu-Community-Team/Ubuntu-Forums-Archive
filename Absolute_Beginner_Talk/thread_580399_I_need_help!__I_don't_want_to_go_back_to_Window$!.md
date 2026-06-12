---
title: "I need help!  I don't want to go back to Window$!"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Ghost Pirate on 2007-10-18
I'm running Ubuntu on an old Dell PC (1.6 GHZ P4, 768 MB RAM, GeForce 2 graphics card, I believe it's Phoenix BIOS revision A06, 80 Gb HDD).  I was having problems with WinXP crashing at seemingly random times.  I re-formatted the HDD and installed Ubuntu hoping to gain more stability.  I fell in love with this operating system!  I found some minor annoyances when I fist started using it; namely that Firefox would randomly close for no reason.  At first, this was no big deal, I could just restart Firefox, restore my last session, and be done with it.  Now, however, once Firefox crashes, it will continue to do so repeatedly.  Last night, I was shopping for hardware on Newegg, and I had to restart Firefox 20 times before I gave up (that is not an exaggeration to get a point across).  Also, Windows XP recognized all of my RAM, even though I have 1 512 and 1 256 stick in the mobo, but Ubuntu only recognizes 503 MB of RAM.  Does anyone have any suggestions to help me?

---

### Post by DGortze380 on 2007-10-18
Your video is most likely using some of your ram. I would try updating firefox, I won't give you terminal prompts because I'm stil learning them myself. Maybe someone else can jump in.

---

### Post by swoll1980 on 2007-10-18
it's flash that causes the problem with firefox go to the mozilla page and down load flashblock, just type it into the search box there. flashblock will allow you to only view the flash that you want too and block the  ads and anoyances

---

### Post by Dr Small on 2007-10-18
Flash is some of the problem, but I my firefox would randomly close for no apparent reason, on the old system too, like this fellow's.

I never did get it fixed, but I think it had something to do with a bad CPU.

Dr Small

---

### Post by p_quarles on 2007-10-18
First, let's look at the RAM issue. Open a terminal and type:
```
free
```
This will list the total amount of RAM, swap memory, and how much is used/free of both. What does it say under the "mem" line in the "total" column?

As for Firefox, there are some tricks to optimize it, but I've found that the easiest thing to do is to replace it with Swiftfox. This is basically just a series of versions of Firefox that are compiled specifically for different architectures. Some people report better speed, but I've found that it's just much more stable than the default Ubuntu version of Firefox. 

You can get it [here]("http://getswiftfox.com/releases.htm"). Select the P4 version, download it, then click on the file to bring up the installation dialogue. It will automatically inherit all your Firefox settings, including bookmarks and extensions, and will not touch Firefox itself.

---

### Post by Dr Small on 2007-10-18
> **p_quarles said:**
> First, let's look at the RAM issue. Open a terminal and type:
```
free
```
This will list the total amount of RAM, swap memory, and how much is used/free of both. What does it say under the "mem" line in the "total" column?

As for Firefox, there are some tricks to optimize it, but I've found that the easiest thing to do is to replace it with Swiftfox. This is basically just a series of versions of Firefox that are compiled specifically for different architectures. Some people report better speed, but I've found that it's just much more stable than the default Ubuntu version of Firefox. 

You can get it [here]("http://getswiftfox.com/releases.htm"). Select the P4 version, download it, then click on the file to bring up the installation dialogue. It will automatically inherit all your Firefox settings, including bookmarks and extensions, and will not touch Firefox itself.
Swiftfox, Firefox, Iceweasel all did the same for me, on the old pc.

---

### Post by p_quarles on 2007-10-18
> **Dr Small said:**
> Swiftfox, Firefox, Iceweasel all did the same for me, on the old pc.
Yeah, I wasn't sure it would help, but it's worth a try I think. Anyway, if that doesn't work, I was going to suggest switching to Opera or Epiphany.

---

### Post by Duck2006 on 2007-10-18
In Gutsy 7.10 look in synaptic and look for swiftwease works great.

---

### Post by Ghost Pirate on 2007-10-23
Thank you to everyone who replied.  Unfortunately, none of the suggestions helped and I was starting to experience more and more crashes with different programs.  A clean re-install did not help either.  After a while, I discovered that the problem was actually a bad mobo.  I rebuilt the system (now with 2.66 ghz P4 processor and 1 GB of RAM) and it's running beautifully, with one exception.  I can barely get online.  The ubuntu forums is all I can access, and only very slowly.  I click a link, wait 5 minutes, and then the page opens.  Every other website times out, so I am limited to just these forums.  I tried manually configuring my network connection, tried Opera and Firefox, all with the same results.  I know I'm connected because updates and add/remove programs download at 256 Kbps.  Anyone know why my browsers can't access the internet?  The settings within the browsers look good.

---

