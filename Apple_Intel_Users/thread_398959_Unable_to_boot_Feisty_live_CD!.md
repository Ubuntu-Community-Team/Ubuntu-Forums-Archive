---
title: "Unable to boot Feisty live CD!"
date: 2007-04-01
forum: Apple Intel Users
---

### Post by ronocdh on 2007-04-01
Obviously not everyone is having this problem, because I know a lot of you are running Feisty (predominantly i386, no?) on your MB(P)s...

When I attempt to boot from the live CD, xserver always fails to start. I've verified the burn of the CD and also checked its integrity through the option listed on the boot screen. I burned again (i386 build), just to be certain. Again, double verified. Again, failed to start X.

Then I tried with the 64-bit Feisty beta, verified in both places, same error! Argh. I'm running a 15" C2D MBP, Radeon X1600. I am trying to jump to Feisty because I haven't gotten full 3D acceleration with fglrx (I have an old Radeon 9200 SE in a tower, so I'm used to the process) in Edgy. 

Any tips?

---

### Post by ronocdh on 2007-04-02
Don't mean to bump, just wanted to state that I've tried the safe graphics version on both i386 and 64-bit, still to no avail. =/ Again, the checksums are all double verified.

I'm not too stressed about it, as I have pretty much everything working under Edgy, but I find it interesting that of all the C2D MBP 15"ers here, I alone seem to be having Feisty issues....

---

### Post by oskarloko on 2007-04-03
I don't know an answer, but maybe a path, using alternate cd install... 

Another linux live distro, like KNOPPIX ?

---

### Post by cyberdork33 on 2007-04-03
I don't understand how you are using fglrx but not getting 3D acceleration... 

There is an issue with X1600 in the iMacs and X. (I thought this was being fixed in Feisty, but maybe not yet).

---

### Post by zorkerz on 2007-04-22
Im getting a problem similar to this if you guys are still around. I have md5sumed the iso then did an integrity check on the cd? (is there a way to md5sum a cd)? 

The boot process appears to go fine then instead of seeing gnome load the screen goes blank. I can still here the music but no screen.

It is possible [this]("http://ubuntuforums.org/showthread.php?t=417566") problem is related but the disc integrity checks out. I plan o testing it on another computer if i get a chance.

Thanks for the help.

---

### Post by bcr88 on 2007-04-22
You're definately not the only person experiencing this problem. I have the exact same problem. I first downloaded the 64-bit version, and got that problem. So I downloaded the 32-bit version thinking it was just a problem with the 64-bit version, but it wasn't. This really sucks! I hope someone can solve this problem!

---

### Post by ronocdh on 2007-04-22
> **bcr88 said:**
> You're definately not the only person experiencing this problem. I have the exact same problem. I first downloaded the 64-bit version, and got that problem. So I downloaded the 32-bit version thinking it was just a problem with the 64-bit version, but it wasn't. This really sucks! I hope someone can solve this problem!
There is hope, my friend! Good ol' michaels had the bright idea of just installing the video drivers from the command prompt (available after X fails to start and you view the output). See his post [here]("http://ubuntuforums.org/showthread.php?t=415959") which links to his blog with a full write-up.

Alternatively (pun kind of intended), you could just install from the alternate CD. This is the route I chose, because I am impatient and foolhardy. :KS It's an all-text installer, but quite intuitive, and the only difference was that I at least got the whole system installed before X tried to run and failed. At that point, I just followed michaels's guide!

---

### Post by zorkerz on 2007-04-22
Hmm im actually able to boot the live cd with the second option for safe graphics. Does anyone know what the difference between these two methods is?
thanks

---

