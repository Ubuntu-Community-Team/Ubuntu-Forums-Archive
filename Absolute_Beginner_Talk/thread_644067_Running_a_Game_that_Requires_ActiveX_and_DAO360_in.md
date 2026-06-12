---
title: "Running a Game that Requires ActiveX and DAO360 in Linux"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Eomi on 2007-12-18
Howdy,

I'm very new to Linux, and so far I'm quite impressed.  In the long run I hope to run my desktop on Ubuntu, but for now I'm just playing around on an old laptop.  So far I've managed to get my graphics card working, and I've installed wine and ie4linux, but I'm still having trouble running a particular program (Bowl Bound 2005) with Wine.  I'm going to be traveling for a month or so, so I'm going to have only my laptop, and while I'm mostly going to be doing work, I would like to get a few games up and running before I head off.

The program installs fine, and launches, but when I go to create a new league I get a RTE that says "ActiveX component can't create object."  The support forums for the game say that I need DAO360.dll, so I downloaded it, but the winecfg application doesn't list it under the libraries tab.  This is where I need help; how can I get wine to recognize dao360.dll?  Is it possible?  Also, I may need Jet 4.0 too, and I'm not sure how to go about getting it.  I've heard of "winetricks," but I fear I may need assistance in setting it up.

Also, I've tried downloading MDAC 2.8, but when I try to install it asks for IE version 4 or later.  I've installed ie4linux and can run ie6, but I don't know how to get the mdac installer to recognize ie4linux.

Last thing, sorry if this doesn't qualify as "absolute beginner."  I am a beginner with Ubuntu, but I know my way around computers pretty well.

Thanks for any help; I hope to learn and become a productive member of the Ubuntu community before too long.

---

### Post by Niniel on 2007-12-18
DAO? Jet?

I  know DAO as a VBA library, and Jet as the dababase engine in Access...

Sorry for this useless post, I'm just very surprised to see these two things mentioned in a gaming context.

---

### Post by Eomi on 2007-12-18
Yeah, I think that's what has complicated this whole procedure.  The game is a text-based simulation, and it uses html reports heavily for output and data storage.  The data files are all compiled with Access (I think for easy modification, I know I've used openoffice to tweak most of the game files), so it uses Jet to access those files.  Obviously the coding of the game is highly unorthodox, which is why I haven't been able to find any info on running it in Linux by searching around.

Anyway, perhaps it's of minor interest to most people, but I'll be sure to track my progress (or lack thereof) here.

---

### Post by stchman on 2007-12-18
> **Eomi said:**
> Howdy,

I'm very new to Linux, and so far I'm quite impressed.  In the long run I hope to run my desktop on Ubuntu, but for now I'm just playing around on an old laptop.  So far I've managed to get my graphics card working, and I've installed wine and ie4linux, but I'm still having trouble running a particular program (Bowl Bound 2005) with Wine.  I'm going to be traveling for a month or so, so I'm going to have only my laptop, and while I'm mostly going to be doing work, I would like to get a few games up and running before I head off.

The program installs fine, and launches, but when I go to create a new league I get a RTE that says "ActiveX component can't create object."  The support forums for the game say that I need DAO360.dll, so I downloaded it, but the winecfg application doesn't list it under the libraries tab.  This is where I need help; how can I get wine to recognize dao360.dll?  Is it possible?  Also, I may need Jet 4.0 too, and I'm not sure how to go about getting it.  I've heard of "winetricks," but I fear I may need assistance in setting it up.

Also, I've tried downloading MDAC 2.8, but when I try to install it asks for IE version 4 or later.  I've installed ie4linux and can run ie6, but I don't know how to get the mdac installer to recognize ie4linux.

Last thing, sorry if this doesn't qualify as "absolute beginner."  I am a beginner with Ubuntu, but I know my way around computers pretty well.

Thanks for any help; I hope to learn and become a productive member of the Ubuntu community before too long.

My advice with Windows gaming is to go game on Windows.  I dual boot on my PCs and use XP for games and Ubuntu for everything else.  If the game plays on WINE then great, but don't count on it.

WINE does not say it is 100% for running Windows apps.

---

