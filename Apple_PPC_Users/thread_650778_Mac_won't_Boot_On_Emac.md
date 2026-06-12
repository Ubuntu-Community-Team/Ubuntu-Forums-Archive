---
title: "Mac won't Boot On Emac"
date: 2007-12-26
forum: Apple PPC Users
---

### Post by Drewmanfuu on 2007-12-26
Uh, hi im kinda new here and ive recently tried to install ubuntu on my old emac and scine the software was so old i decided to try ubuntu which ive used on my windows computer. Im a total noob when it comes to macs, cause ive never used em before so could someone help me out? I think ive tried everything but it just wont boot on my emac, ive used the C key i tried using a diff cd drive, the different key combintations on startup but nothing seems to work, if anoyone could help me out i would greatly apreciate it, thank you    SORRY UBUNTU WONT BOOT ON EMAC, NOT MAC WONT BOOT

---

### Post by Auria on 2007-12-27
Also try the alt key at startup

1) make sure you have burned the PPC CD, the CD you use for windows machines won't work
2) make sure you burnt slowly (4X is usually recommended)
3) check the checksum of the download to make sure your iso is okay
4) make sure you burnt the contents of the iso on a CD (copying the iso file onto a CD won't work, the disk utility program that comes with OS X can burn that properly)

---

### Post by Drewmanfuu on 2007-12-27
Well, i downloaded and installed the ppc version, like you said, i hit enter and it started to go thru some black and white screens then to the Ubuntu logo with the installation prorgress bar thing, however the color was completely of like something was wrong and it didn't take up the whole screen, only about 1/4 like it was not centered right. Anyway it started to the installation bar thing started moving but stopped about a 3rd of the way there and rebooted. I tried it again with the same results. no luck, any suggestions?

---

### Post by Drewmanfuu on 2007-12-27
ok, so i tried an older version of ubuntu like 6.10 (just so you know i was using 7.04) and same deal, got to the off color off center install bar thing with logo however it completley filled the install bar then after that it went balck. The cd was still going, i could hear it, then i heard music like it was installing but i couldnt see anything???:confused: any suggestions here?

---

### Post by oswaldkelso on 2007-12-28
> **Drewmanfuu said:**
> ok, so i tried an older version of ubuntu like 6.10 (just so you know i was using 7.04) and same deal, got to the off color off center install bar thing with logo however it completley filled the install bar then after that it went balck. The cd was still going, i could hear it, then i heard music like it was installing but i couldnt see anything???:confused: any suggestions here?

maybe X has failed? you could try  keys 

CTL+ALT+F1 

This will give you a shell then check your xorg.conf file see link


[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

the screen resolution for most emacs (ati) is   
71-73 for vertical and 70-140 horizontal.
 Also although emacs support screen resolutions 1280×960 and 1152×870 only 1024×768 ever shows up? Just make sure 1024×768 is selected.

attached is my emac xorg.conf  so you can compaire  I'm running debian so I dont know if its the same as an ubuntu one but the main specs should be the same

---

### Post by dcast on 2007-12-29
Hey I have an eMac, ubuntu will pretty much not run on it. Mine is the model with an ATI graphics card. I would recommend trying openSuSE 10.3 which ran on my machine almost without a hitch except for sound which is now working fine. 

try:  [www.opensuse.org](www.opensuse.org) and download either the DVD image for PPC or try the network install CD.

---

### Post by Drewmanfuu on 2007-12-30
well I scince ive been trying to hard on ubuntu and pretty much have given up i dowloaded the opensuse software and burned it to a DVD but everytime i put the dvd into my emac it keeps taking a couple seconds and spitting it back out, any ideas whats goin on?

---

### Post by Drewmanfuu on 2008-01-09
Anyone???

---

### Post by joe_bloe on 2008-01-19
I have an eMac also, don't know much about it.  It's a G4 1.25GHz.  I couldn't get Gutsy to work on it, either the live cd or the alternate install.  It appeared to be a video problem.  However, Feisty alternate install worked fine, with the exception of the sound, which I haven't worked out yet.

---

### Post by jaw1959 on 2008-01-20
I just my hands on 2 800mhz G4 eMacs.  I plan to use one for a mythtv frontend.  I have the mac build working on one, but the other doesn't seem to work as well (one has 512mb of ram, the one that works well, but the other has 256mb).  I did some research, and they were supposed to have nvidia geforce 2 graphics cards, but it appears they have ATI RV200 cards.  I have an disc of the PPC version of 6.10, but it fails to load x when it boots.  To make it boot, all I had to do was hold "c" when the machine turned on.  Does anyone know where to find another PPC install disc?

---

