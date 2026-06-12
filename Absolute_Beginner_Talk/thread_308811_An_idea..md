---
title: "An idea."
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by launcherx on 2006-11-28
Hello am. I am a new user to this Linux package and I must say that it is quite amazing. The others are not as facinating as this. I have something I'd like to share, and this is an idea. I think that for the upcoming Ubuntu versions they should implement an *.msi/*.exe emulator. Wine, from what I have read is a good choice. I think it should be used. It would be nice to actually run *.exe and *.msi files on a linux system. It'll make some if not most people feel more at home. This OS is awesome though. No doubt about it.

---

### Post by atoponce on 2006-11-28
WINE is already available to those who want to run Windows binaries on their system.

sudo aptitude install wine

---

### Post by scrooge_74 on 2006-11-28
Then you should give wine a try or cross over office. A lot of programas from windows run very good

---

### Post by mdsmedia on 2006-11-28
> **launcherx said:**
> Hello am. I am a new user to this Linux package and I must say that it is quite amazing. The others are not as facinating as this. I have something I'd like to share, and this is an idea. I think that for the upcoming Ubuntu versions they should implement an *.msi/*.exe emulator. Wine, from what I have read is a good choice. I think it should be used. It would be nice to actually run *.exe and *.msi files on a linux system. It'll make some if not most people feel more at home. This OS is awesome though. No doubt about it.As a long time Windows user and a Linux newbie, I don't think this is really a good idea. As others have already said, Wine is available as an "emulator" and is easily installed.

Linux is not Windows and trying to make it more Windows-like is not a goal, from what I can tell, of the Ubuntu project. It is a goal of the Wine project, so install Wine if you want it, but I don't believe a default install is necessary or even desirable.

---

### Post by xopher on 2006-11-28
Agreed, if wine was installed by default - even configured for easily installing windoze apps -- it wouldn't be the same ubuntu as I know it today. Linux is Linux and Windoze is Windoze. In my opinion we should keep it that way..

---

### Post by PriceChild on 2006-11-28
WINE - Wine Is Not (an) Emulator...

I don't see any reason to include wine by default.

Not only is there the issue of disk space... but why promote this? wine doesn't work very well at best and is very hit and miss. Much better alternatives exist to windows apps.

Pricey

---

### Post by scrooge_74 on 2006-11-28
> **PriceChild said:**
> WINE - Wine Is Not (an) Emulator...

I don't see any reason to include wine by default.

Not only is there the issue of disk space... but why promote this? wine doesn't work very well at best and is very hit and miss. Much better alternatives exist to windows apps.

Pricey

You are right but from time to time you need some windows apps, I look around and still I prefer to use Peachtree for my accounting than what I found on Linux.

I am still fond of a couple of games.

---

### Post by xpod on 2006-11-28
Dualbooting is a great thing:mrgreen:

---

### Post by scrooge_74 on 2006-11-28
I gave away my last XP CD, so I can't go back :D

---

### Post by IYY on 2006-11-28
Wine is not reliable enough to be included by default. It would lead to users telling their friends: ``Ubuntu can run Windows programs'', and when they see how buggy this feature is, they will dislike Ubuntu and Linux in general.

---

### Post by atoponce on 2006-11-28
> **xpod said:**
> Dualbooting is a great thing:mrgreen:

Or running Windows in a VM with Ubuntu as the host OS.

---

### Post by LLRNR on 2006-11-28
> **launcherx said:**
> It would be nice to actually run *.exe and *.msi files on a linux system. It'll make some if not most people feel more at home.

The goal is to realize (and eventually accept) the fact that [Linux is NOT Windows](http://linux.oneandoneis2.org/LNW.htm).

Despite the fact that it's not such a good idea, as a quick tech note, the problem of running exe and msi installers NATIVELY in Linux is not as smooth at it might appear to you. 

First off, think about the fact that Linux and Windows each run on different filesystems. Second, think about the way that these OSs handle the files. The structure of executables is fundamentally different in Linux and in Windows. If exes and msis were to run natively on Linux, then it would mean that in the best case scenario we'd have a hybrid Linux filesystem; which means turning Linux into Windows; which is not the goal. Linux is not meant to be a substitute, but an alternative; an alternative is another way of doing things, and not just mere copying a given template.

LLRNR

---

### Post by scrooge_74 on 2006-11-28
> **atoponce said:**
> Or running Windows in a VM with Ubuntu as the host OS.

Not enough RAM to even think about it

---

### Post by mdsmedia on 2006-11-28
> **PriceChild said:**
> WINE - Wine Is Not (an) Emulator...
That's why I put "emulator" in quotes....for want of a better word I guess :) 

> I don't see any reason to include wine by default.

Not only is there the issue of disk space... but why promote this? wine doesn't work very well at best and is very hit and miss. Much better alternatives exist to windows apps.
PriceyAgreed. Why promote the use of Windows software? 

I use Wine to run ONE program, only because I've used it for 10 years and am an operator in an IRC help channel for it. I still haven't got it working very well under Wine, but that's just me...another challenge ;)

---

### Post by PriceChild on 2006-11-28
> **mdsmedia said:**
> I use Wine to run ONE program, only because I've used it for 10 years and am an operator in an IRC help channel for it. I still haven't got it working very well under Wine, but that's just me...another challenge ;)
What program is this?

---

### Post by turbojugend_gr on 2006-11-28
Linux is all about choice, and freedom of it. So a default windows-to Linux api transalator (that's what Wine is), is only bad due to the brainwash windoz put us through. If it was trully a free market (the software market I mean) then a default wine would hurt nobody, but since it isn't and most companies (or even countries!) just "assume" you have windoz, giving 'em another arguement (Linux has an api translator, so wh should I care).

The thing that would mostly violate freedom, has to do with a new user. Users tend to believe (correctly) that an app is by default into an OS, cause it's an essential part of it, for example windwos can't work without windows media player-yet vlc runs on windoz too-yet it isn't the default. What I mean is a user would be falsely given the impression Linux needs Wine, and this is obviously createing the impression Linux is a free way to use all my windows stuff, so Linux is a bunch of free crap (nah, since it's free I may use it..). I tried to make my point here, I guess i failed, but it's late....;)

---

