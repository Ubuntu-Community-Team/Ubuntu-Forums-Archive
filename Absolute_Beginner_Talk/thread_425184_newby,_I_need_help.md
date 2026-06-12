---
title: "newby, I need help"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by neanderthal on 2007-04-27
Hi, I'm Dan

I'm not entirely new to linux... but am new to administering a linux system, I'm a bit overwhelmed by the vastness of this forum and appologise if this has been covered before.

OK so I am traditionally a mac user, but recently purchased a pc.

(This will get to ubuntu)I had no trouble installing fedora core 6, but had trouble with the driver for my iburst modem... after much googling I discovered that the support community for ubuntu is better and there's even a how to guide on this forum for the iburst driver.

The trouble is, as my user name suggests I am a neanderthal and can't seem to install ubuntu over fedora core 6.

Since the how to iburst guide only goes up to edgy 6.10 that's what I am going with, but also have the 7.04 version if needed. I don't know how much info to give, I've got limited RAM, but it meets requirements.

I'm on an acer aspire 3610 with a pentium M processor.

---

### Post by Zuuswa on 2007-04-27
Well, what is the problem you are having?? Im not sure how to help if I dont know whats going wrong.  Can you be more specific than "Can't seem to install ubuntu"?

---

### Post by Cypher on 2007-04-27
If you downloaded and burnt the LiveCD versio of Edgy (6.10) or Feisty(7.04) then pop that in and boot into Ubuntu, if everything works fine. Then double-click on the Install button on the desktop and either use the existing Fedora Core partitions (make sure to format them) or delete them all and re-create partitions for Ubuntu and you should be rolling in no time..

---

### Post by neanderthal on 2007-04-27
I put the cd in, reboot. I tell it to start/install ubuntu, I get a screen with a progress bar, it waits a while. Loads the live desktop OK, but when I click the "install" icon it freezes up completely, not even the off button works. Being a laptop I had to wait for it to go flat because I couldn't unplug it to force a reboot...

I don't know if thats any more helpful?

---

### Post by Cypher on 2007-04-27
Can you give us the specs on your laptop, it's annoying that the power button wouldn't work. Can you take out the battery and run purely on AC so you can pull the plug if it happens again??

---

### Post by airtonix on 2007-04-27
yeah to shutdown most modern computers (laptop or desktop) you hold the power button down for five seconds or more.

if it shutsdown before five seconds it may be in a soft shutdown or a standby mode, bring it out of that mode and immeadiatly hold down the power button for five seconds.

if and when you try this install again, try this also for trouble shooting : > ctrl + alt + 3it should change your view to a fullscreen terminal. if you can get here then there is hope for your case yet as far as i know

---

### Post by neanderthal on 2007-04-27
Shows how dumb I am I never would have thought of the battery thing!

Specs:

Intel Pentium M processor 735A 1.7 ghz

256 mg RAM

40 gig HD

I'll have to find the manual if you need more than that

I'll try the battery thing now

---

### Post by lamalex on 2007-04-27
also there is always my personal favourite the alternate install cd. I prefer it very much to the live cd.

---

### Post by neanderthal on 2007-04-27
at what point do I press ctrl + alt + 3? On the first screen?

---

### Post by Cypher on 2007-04-27
You're fine as far as CPU and HD space goes, but I think you might be running near the limit of what Ubuntu with GNOME needs. You might have better luck running Xubuntu with XFCE..

---

### Post by neanderthal on 2007-04-27
I tried again and it didn't freeze straight away, but eventually did.

So I tried ctrl+alt+3 on the first screen and that eliminated the time limit to select a choice but did nothing else...

---

### Post by neanderthal on 2007-04-27
> **Cypher said:**
> You're fine as far as CPU and HD space goes, but I think you might be running near the limit of what Ubuntu with GNOME needs. You might have better luck running Xubuntu with XFCE..

Because I'm on a very old computerATM  without my good computer up and running I can't download xbuntu, but I can upgrade the RAM if thats the problem, I've been meaning to since I got it

---

### Post by Cypher on 2007-04-27
I can't say it's going to make your problem go away, whatever it is,  but I think you'll have a better shot at getting this going with more memory. THOUGH, since the LiveCD came up, I would imagine that it's OK for it to operate..but if you have the memory, no harm in doing the upgrade and trying again..

---

### Post by airtonix on 2007-04-27
you use the key combo when the install fails...(the icon you click on the desktop)
 if it doesnt respond then you are better off downloading the alternate install cd like the fellow before me mentions


meh 1.7ghz is more than enough for gnome...
but 256 mb ram is enough for the desktop only, and maybe one programe. hehe 

If you want gnome to be quick, responsive and allow you to work in maximum comfort you will need a minimum of 1gb sdram.
if you want a quick graphical gui desktop for your current hardware, then you will want to look at xfce4, it is quite mature and also has the basic compiz effects available for use.

my pentium 4 1.6ghz with 512mb ddr ram play world of warcraft in the most fantastic fashion. and it handles beryl well for about three applications....then it all goes downhill. response times extend and extend. i also tried the xfce4 combination of compiz, and it was much faster.but still metacity was faster with more apps...

go with xfce4 becuase it handles all of the gnome applications anyway...and its so damn fast too.

---

### Post by neanderthal on 2007-04-27
I'm in a full screen terminal now after pressing ctrl+alt+F3

---

### Post by neanderthal on 2007-04-27
So what do I do now?

---

