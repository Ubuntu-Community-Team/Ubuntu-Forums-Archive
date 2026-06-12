---
title: "Fresh Ubuntu 7.10 gives me Black Screen (of death?)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by CostaRica on 2007-10-22
I have a Laptop Sony VAIO VGN-A190 with:
- 2Gb RAM
- ATI Radeon 9700
- 1920x1200 17" Screen
- 80Gb HDD

1. I made a fresh install of WinXP Pro, defragmented the HDD and installed Ubuntu 7.10 as a dual-boot.
2. When I boot Gutsy I get a white screen the turns into a black screen, but WinXP Pro still works fine.
3.  No prompt, no nothing on Gutsy.
4. Feisty Ubuntu 7.04 worked PERFECTLY.  Are we going backwards (Vista Style)?

Can you help me, please?

P.S.  I tried hard not to repeat the thread, but could not find instructions for my case.  Thanks!

---

### Post by Dr Small on 2007-10-22
> **CostaRica said:**
> I have a Laptop Sony VAIO VGN-A190 with:
- 2Gb RAM
- ATI Radeon 9700
- 1920x1200 17" Screen
- 80Gb HDD

1. I made a fresh install of WinXP Pro, defragmented the HDD and installed Ubuntu 7.10 as a dual-boot.
2. When I boot Gutsy I get a white screen the turns into a black screen, but WinXP Pro still works fine.
3.  No prompt, no nothing on Gutsy.
4. Feisty Ubuntu 7.04 worked PERFECTLY.  Are we going backwards (Vista Style)?

Can you help me, please?

P.S.  I tried hard not to repeat the thread, but could not find instructions for my case.  Thanks!
Hello, Your problem sounds similar to mine.
Please take a look at this thread here, as it may help :)
[http://ubuntuforums.org/showthread.php?t=586962](http://ubuntuforums.org/showthread.php?t=586962)

Dr Small

---

### Post by CostaRica on 2007-10-22
I get into graphics mode when I do

startx -- :1

while in recovery mode, but when I re-boot, again the Black Screen goes down on me...

---

### Post by CostaRica on 2007-10-22
How do I install the restricted ATI driver from the terminal?

---

### Post by CostaRica on 2007-10-22
Do I need the xorg-driver-fglrx?  How do I get it?

---

### Post by adamorjames on 2007-10-22
> **CostaRica said:**
> Do I need the xorg-driver-fglrx?  How do I get it?

Not sure you need it but if you do then type, "sudo apt-get install xorg-driver-fglrx" into a terminal or CLI of some sort.

---

### Post by CostaRica on 2007-10-22
It says Couldn't find package xorg-driver-fglrx.

I really do not really know what I am doing.  I just need to know how to install an ATI Radeon 9700 because I suppose that is the problem.  Any suggestion?

---

### Post by CostaRica on 2007-10-22
I have read about people getting the black screen from the live-CD, but the live-CD works great.  The problem comes when I install Gutsy.

---

### Post by adamorjames on 2007-10-22
> **CostaRica said:**
> It says Couldn't find package xorg-driver-fglrx.

Interesting, I have the package. Bump.
EDIT: Could be a Compiz problem... may need to disable it not sure how... maybe an uninstall.

---

### Post by CostaRica on 2007-10-22
Could it be that the network card is not working neither?

---

### Post by adamorjames on 2007-10-22
> **CostaRica said:**
> Could it be that the network card is not working neither?

Yes, it could be. Bump.

---

### Post by CostaRica on 2007-10-22
Any advice on how to check that?

P.S. What's with the BUMP thing?

---

### Post by adamorjames on 2007-10-22
> **CostaRica said:**
> Any advice on how to check that?

P.S. What's with the BUMP thing?

Not sure how to check it. I'm not a Linux CLI master yet :lol:.

P.S. The bump thing is what some people say when they are moving the thread up higher (by posting) to get noticed. :)

---

### Post by CostaRica on 2007-10-22
I am like 10 minutes from asking how to un-install gutsy and go back to feisty, with which I did not have any problem.  I have been trying to get gutsy working since October 18th and have spent countless hours  formating time and again my laptop.

---

### Post by adamorjames on 2007-10-22
> **CostaRica said:**
> I am like 10 minutes from asking how to un-install gutsy and go back to feisty, with which I did not have any problem.  I have been trying to get gutsy working since October 18th and have spent countless hours  formating time and again my laptop.

Yeah, I think the best option for you is to go back to Feisty. Put in the Live CD, restart and install. Make sure you have your home folder as a separate partition before you install.

---

### Post by CostaRica on 2007-10-23
Should I have /home in a separate partition because of personal information or because feisty won't install any other way?

---

### Post by shae on 2007-10-23
You might want to have it so you can preserve settings and files between reinstalls/upgrades.

---

### Post by angelsneverdie on 2007-10-23
I installed gutsy (fresh install) and when It restarts to boot up all I get is a blank screen.  i've got an ati radeon mobility m6 ly card - p4 2.2ghz

i tried reconfiging the xserver as per advice in a different post, and after i typed 'startx' it booted in a privliged login?? but upon restart still get black screen.

any ideas?

---

### Post by angelsneverdie on 2007-10-23
buried so quick  . . .

bumpy bumpy

---

### Post by adamorjames on 2007-10-23
> **CostaRica said:**
> Should I have /home in a separate partition because of personal information or because feisty won't install any other way?

So your personal files don't get deleted.

---

