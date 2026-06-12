---
title: "Will Linux ever be able to run xp games?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-08-09
as what it says in the title... will it ever be able to run xp games? perhaps in vmware sometime in the future.. anyone know ?

---

### Post by toidi on 2007-08-09
Yes it will.  I got WOW to work in linux using wine ([www.winehq.com](www.winehq.com)).  Took a bit of work at first but running sweet now.

Also got Lord of the rings online to work as well (that one only took 20 minutes to sort after my first experience).

---

### Post by aldenhg on 2007-08-09
It kinda is able to - depending on your definitiion of the word "run." You can use tools like Wine and Cedega to run games. Both work by implementing a reverse-engineered version of the Windows API that is compatable with Linux to run the games. Wine is still considered beta software, despite years of development and Cedega is a commercial program that you can pick from [www.transgaming.com](www.transgaming.com). Both require at least a bit of work to get running and in my experience are not for the faint of heart. You can get Wine by opening up a terminal and running sudo apt-get install wine. Beyond that I can't help you since I'm muddling through it myself.

---

### Post by jake16424 on 2007-08-09
> **Likenota said:**
> as what it says in the title... will it ever be able to run xp games? perhaps in vmware sometime in the future.. anyone know ?

no. for the simple fact that linux, tells the processor to work differently than windows does. therefore, it wouldnt work, without an emulation tool like wine. wich doesnt work, unless you have ubuntu or another linux based os using 32bit only....



keep in mind im not a programmer.

---

### Post by Jimmyfj on 2007-08-09
Yes it will be possible to run Windows games on Linux - I've got Return to Castle Wolfenstein running in Wine, same goes for Doom2 - So the answer must be Yes!

---

### Post by aysiu on 2007-08-09
Yes. Ten years from now, I'm betting Linux will be able to run all the XP games. Of course, by that time, no one will want to play XP games any more than people want to play Windows 95 games now.

---

### Post by ahchong on 2007-08-09
not exactly YES!. cause i cant play my MU online on fiesty 64-bit. so, stil NO!. Wine is far from complete version yet... if anyone play MU could tell me the proper way to play it..

---

### Post by foxholeunder on 2007-08-09
The day that NVIDIA or ATI release a codebase to the opensource community that allows access to all the features of their chipsets...IE: 3D drivers... will be the day that game developers will seriously consider releasing game versions that will install and run on Linux-based distro's  natively. 

Otherwise, most all popular games are playable via Wine and Cedega. 

Cedega has more supported games that install without many workarounds over Wine, but Wine with workarounds supports more games overall.

Wine is free and Cedega charges for their software. It is fairly cheap though and you can install a trial version to check it out and see if you like it. 

If the games you are desiring to run work with Wine fairly easily or you don't mind getting your hands dirty and doing a little research on how others have gotten the game to work then I would go with Wine. 

I have about 50 or so games installed with wine and they all run smooth. Most installed with little or no trouble, and only a small handful required some 'extra' tweaking to complete the installation. Like I mentioned though, they have all ran smoothly after install.

---

### Post by cobrn1 on 2007-08-09
> **aysiu said:**
> Yes. Ten years from now, I'm betting Linux will be able to run all the XP games. Of course, by that time, no one will want to play XP games any more than people want to play Windows 95 games now.

True, true...

WINE and Cedega are options, and although they are abit hit-and-miss, they're worth a shot. Basically, many games work, many don't, but you've got to appreciate that linux is a different OS, it works differently and needs it's own versions of games to work properly...

Om the plus side a few top rated games are getting linux releases soon (quake wars and UT3) so the future of linux gaming is looking up... slightly.:)

---

### Post by Likenota on 2007-08-10
hmm by any chance does wine work with counter strike.. how on earth did u get it to work with doom3 ???? is there a place where it shows how to install this stuff..

---

### Post by toidi on 2007-08-10
I believe you can get steam to work with wine, all the source engine games work.
Doom3 has native linux support. ie. you can download a doom3 client for linux (just google it).

Oh and a link to installing steam under wine [http://appdb.winehq.org/appview.php?iVersionId=1554&iTestingId=14037](http://appdb.winehq.org/appview.php?iVersionId=1554&iTestingId=14037)

Hope this helps.

---

### Post by WebSiteGuru on 2007-08-10
By any chances if anyone got Diablio2 to work on wine? I am having problem with it getting stuck on install screen. I know at winehq it said that it works. :confused:

---

### Post by Ek0nomik on 2007-08-10
> **WebSiteGuru said:**
> By any chances if anyone got Diablio2 to work on wine? I am having problem with it getting stuck on install screen. I know at winehq it said that it works. :confused:

[http://ubuntuforums.org/showthread.php?t=122861](http://ubuntuforums.org/showthread.php?t=122861)

[http://ubuntuforums.org/showthread.php?t=362457](http://ubuntuforums.org/showthread.php?t=362457)

---

### Post by asmoore82 on 2007-08-10
> **jake16424 said:**
> no. for the simple fact that linux, tells the processor to work differently than windows does. therefore, it wouldnt work, ***without an emulation tool like wine***. wich doesnt work, unless you have ubuntu or another linux based os using 32bit only....

keep in mind im not a programmer.

WINE = Wine Is Not an Emulator.

---

### Post by 9a3eedi on 2007-08-10
Counter Strike works properly with wine, from what I tried out. Counter Strike Source may give you problems though. Steam is also annoying with Wine

as for doom 3, it can run native in linux. No need for wine. Go to this website:
[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)
to find out more

you will need to download an installer, copy some files from the doom 3 CD's, and most of the time it will work. You may need to switch to oss for sound though, but that's easy to fix

---

### Post by 9a3eedi on 2007-08-10
> **Jimmyfj said:**
> Yes it will be possible to run Windows games on Linux - I've got Return to Castle Wolfenstein running in Wine, same goes for Doom2 - So the answer must be Yes!


Doom 2 doesn't require wine to run. Install PrBoom or some other open source doom engine, then copy the wad files, and it works.. with sound and everything

I got shareware doom to work on linux using PrBoom. and it's even better. You can use OpenGL for 3D rendering for example, anti aliasing, texture filter, etc. Also it supports timidity, which is awesome.

---

### Post by irish_flu on 2007-08-10
> **aysiu said:**
> Yes. Ten years from now, I'm betting Linux will be able to run all the XP games. Of course, by that time, no one will want to play XP games any more than people want to play Windows 95 games now.

Seconded.  By the same token, we'll soon start seeing games that can't run in XP (and require Vista).

---

### Post by toidi on 2007-08-10
> **irish_flu said:**
> By the same token, we'll soon start seeing games that can't run in XP (and require Vista).

Halo 2 will be vista only.

Ironic that when dx10 support is released for wine then xp users could be able to play halo2 using wine.  If not then they might have to come over to linux to play them (if indeed they get it working in linux/wine) :D

---

### Post by MenZa on 2007-08-10
> **9a3eedi said:**
> Counter Strike works properly with wine, from what I tried out. Counter Strike Source may give you problems though. Steam is also annoying with Wine.


Not at all. I've run CS: Source, DoD: Source and Half-Life 2. Plus a variety of custom mods, but they do require a slightly higher-end PC than Valve recommends, due to the emulation taking place. (Yes, wine is a compatibility layer, but it /does/ use resources to emulate running it.)

> **toidi said:**
> Halo 2 will be vista only.

Ironic that when dx10 support is released for wine then xp users could be able to play halo2 using wine.  If not then they might have to come over to linux to play them (if indeed they get it working in linux/wine) :D

I do assume you mean Halo 3? ;)

---

### Post by toidi on 2007-08-10
You would have thought it would have been halo3 but alas tis microsoft and it i*is* halo 2 vista only ;)

---

### Post by MenZa on 2007-08-10
> **toidi said:**
> You would have thought it would have been halo3 but alas tis microsoft and it i*is* halo 2 vista only ;)

Aha; according to Wikipedia, Halo 2 was re-released in 2007 (thought the original release was in 2004 for consoles). I see. I guess you learn something every day.

---

### Post by asmoore82 on 2007-08-10
> **MenZa said:**
> Not at all. I've run CS: Source, DoD: Source and Half-Life 2. Plus a variety of custom mods, but they do require a slightly higher-end PC than Valve recommends, **due to the emulation taking place**. (Yes, wine is a compatibility layer, but it /does/ use resources to emulate running it.)

WINE = Wine Is Not a %#@$ Emulator!

[http://www.winehq.org/site/myths#slow](http://www.winehq.org/site/myths#slow)

---

### Post by MenZa on 2007-08-10
> **asmoore82 said:**
> WINE = Wine Is Not a %#@$ Emulator!

[http://www.winehq.org/site/myths#slow](http://www.winehq.org/site/myths#slow)

Wine is slower than running the application on the platform it's intended to be run on. And yes, Wine is no emulator, but that's exactly what I state. An emulator and a compatibility layer are two different things.

---

### Post by aldenhg on 2007-08-10
I keep seeing peope using the word 'emulation' . Let's make something perfectly clear: WINE is not an emulator and neither is Cedega. They are reverse engineered APIs that allow Windows programs to run in Linux NATIVELY. Emulation only happens in virtualization - like when you run Windows in VMWare. 
Because there is no emulation happening games that your hardware meets the specs for will work just fine if they're supported by Wine or Cedega. In fact, there have been reports of people getting higher framerates in Linux then they do in Windows.

---

### Post by splintercellguy on 2007-08-10
> **jake16424 said:**
> no. for the simple fact that linux, tells the processor to work differently than windows does. therefore, it wouldnt work, without an emulation tool like wine. wich doesnt work, unless you have ubuntu or another linux based os using 32bit only....



keep in mind im not a programmer.

Wine is not an emulator. It simply parses a Windows PE file in a way that can be handled by the kernel and maps imports to Wine's implementation.

---

### Post by bodhi.zazen on 2007-08-10
Linux already runs windows XP games ....

[http://gaming.gwos.org/news.php](http://gaming.gwos.org/news.php)

---

### Post by Jonnothin on 2007-08-10
> **toidi said:**
> Halo 2 will be vista only.

Ironic that when dx10 support is released for wine then xp users could be able to play halo2 using wine.  If not then they might have to come over to linux to play them (if indeed they get it working in linux/wine) :D

I'm sorry but vista is worse than XP(5% slower with updates) so Windows is going to have to make a new OS to catch up, because if they wait to long linux will leave them in the dust. But otherwise I agree

---

### Post by splintercellguy on 2007-08-10
> **bodhi.zazen said:**
> Linux already runs windows XP games ....

[http://gaming.gwos.org/news.php](http://gaming.gwos.org/news.php)

Link's broken.

---

### Post by asmoore82 on 2007-08-10
> **MenZa said:**
> Wine is slower than running the application on the platform it's intended to be run on. And yes, Wine is no emulator, but that's exactly what I state. An emulator and a compatibility layer are two different things.

that's not neccissarily true, read what they say more carefully ...

> Windows applications that do not make system calls will run just as fast as on Windows (no more no less).
Some people argue that since Wine introduces an extra layer above the system a
Windows application will run slowly. [I][B]It is true that, in theory, Windows applications that run
in Wine or are recompiled with Winelib will not be able to achieve the same performance
as native Unix applications.[/B][/I]

App X written for Windows and ran on WINE on UNIX will run slower than App X written for UNIX.
But App X written for Windows will run the same on Windows and WINE on UNIX.

---

### Post by stinger30au on 2007-08-10
you can do it now. get win4lin pro. install xp inside ubuntu and go for it

---

### Post by lyceum on 2007-08-10
> **aysiu said:**
> Yes. Ten years from now, I'm betting Linux will be able to run all the XP games. Of course, by that time, no one will want to play XP games any more than people want to play Windows 95 games now.

lol! That is awesome!

Really though, I think that Wine is getting better, Ubuntu is being sold by Dell and alt OS's are being taken more seriously. Look at the Mac when it first came out vs. now. Just wait. Things are getting better all the time!

---

