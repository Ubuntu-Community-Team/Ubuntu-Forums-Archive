---
title: "How to diagnose random freezing?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Scoodaddy on 2007-06-23
I have a pretty basic Ubuntu 7.04 installation, and sometimes it suddenly and completely freezes on me:  no response at all to mouse and keyboard, no hard disk activity, even after a long time, so the only thing I can do is a hard reset.  It happens seemingly randomly: sometimes when I open a browser tab in Firefox, sometimes when I open a folder on the hard disk, sometimes something else.  Consequently I have no clue what the cause is.  Can anyone suggest a way to begin diagnosing the problem?  A particular log file I should check, for example?  BTW, I'm running the open source "ati" driver, and while I have installed beryl I am not usually running it when the crashes occur.  Thanks!

System specs:
Athlon 64 X2 4400+
Asus A8V mobo 
1GB DDR400 RAM 
ATI Radeon 9600XT

---

### Post by p_quarles on 2007-06-23
Are you running the 64-bit version, or the 32-bit version? If the former, the first thing to find out is if the 32-bit OS is more stable on your system. 

Aside from that, it's sometimes useful to run all your apps from the command line. Doing this gives the terminal a chance to tell you what's wrong.

---

### Post by Scoodaddy on 2007-06-23
I should have added: it's the 32 bit version.  Good idea about the command line, but the last time it happened (half an hour ago) all I did was open a new tab in Firefox, which had been running fine up until that moment.  I can't open a new tab in FF from the command line (can I?)  And unfortunately I can't seem to reliably reproduce the problem, I just know it will happen eventually.

---

### Post by Crafty Kisses on 2007-06-23
> **Scoodaddy said:**
> I have a pretty basic Ubuntu 7.04 installation, and sometimes it suddenly and completely freezes on me:  no response at all to mouse and keyboard, no hard disk activity, even after a long time, so the only thing I can do is a hard reset.  It happens seemingly randomly: sometimes when I open a browser tab in Firefox, sometimes when I open a folder on the hard disk, sometimes something else.  Consequently I have no clue what the cause is.  Can anyone suggest a way to begin diagnosing the problem?  A particular log file I should check, for example?  BTW, I'm running the open source "ati" driver, and while I have installed beryl I am not usually running it when the crashes occur.  Thanks!

System specs:
Athlon 64 X2 4400+
Asus A8V mobo 
1GB DDR400 RAM 
ATI Radeon 9600XT

Possible resource issue?

---

### Post by p_quarles on 2007-06-23
> **Scoodaddy said:**
> I should have added: it's the 32 bit version.  Good idea about the command line, but the last time it happened (half an hour ago) all I did was open a new tab in Firefox, which had been running fine up until that moment.  I can't open a new tab in FF from the command line (can I?)  And unfortunately I can't seem to reliably reproduce the problem, I just know it will happen eventually.
You can't open a new tab in CLI, as far as I know, but it still might give you feedback if you leave the terminal open. 

Dunno, though. I haven't had that problem, so I'm just giving you my best guess.

---

### Post by Scoodaddy on 2007-06-23
> **Codename said:**
> Possible resource issue?

Hmm, how could I tell?  Anything I can do to test it?

---

### Post by orb9220 on 2007-06-23
It is just a matter of isolating.

1) First thing is to run without Beryl or Compiz 3d enable effects. Turn them off.
2) install Opera,ephiany,etc for another browser and use that for awhile.
3) Turn off screensaver's and leave desktop running without torrent's or browser open to see if it locksup on it's own.

These suggestions might help you isolate an app or a bug in the kernel.

Others having these problems have varying suspicions from Kernel,video drivers,Beryl, and Firefox as the culprits.

---

### Post by Inxsible on 2007-06-23
My system freezes randomly too. I use Opera which freezes up too. But my Beryl is almost always running during the crash. I have had freezes only when RhythmBox was runningand no browsers were open. 

So my guess is Beryl being the culprit. I shall try to see if i get those random freezes without Beryl

---

### Post by Maxtorm on 2007-06-23
Another possibility is a bad power supply.  Replace it as a last resort.  It has fixed more than one "random freezing" in the environment I support.

---

### Post by Inxsible on 2007-06-24
> **Maxtorm said:**
> Another possibility is a bad power supply.  Replace it as a last resort.  It has fixed more than one "random freezing" in the environment I support.

I just bought this laptop brand new about 3 months ago. I dont think it would be a power issue. Moreover it doesnt happen in my Vista boot

---

### Post by tgalati4 on 2007-06-24
I would run memtest overnight--100 complete cycles at least.  It's in the option menu on the Live Disk.  I would also burn a Dapper 6.06.1 Live Disk and run that.  See how many days you can go before you get a lock-up.  I bet it's several weeks.

You can mount your hard disk using the Live CD and still have access to your data, you just won't have your desktop customized the way you want.  With a freeze-up problem, desktop configuration is low on the priority list.

Let us know the results of your testing then we can proceed to the next step.  It's tedious, but you have to be methodical to pin down the problem.

---

### Post by Scoodaddy on 2007-06-24
Thanks, I'll give these suggestions a try.  I don't think it's a hardware problem, as I dual boot the machine with Windows XP and I never have these freeze-up problems -- which is NOT to say I prefer Windows :)  And I doubt it's Beryl related as I usually don't even run Beryl (can it cause problems just by having the package itself installed?)  But I like the idea of running off the Ubuntu Live CD for a while and seeing what happens.  And maybe I'll run it for a while with the flgrx drivers installed.  I'll give it a try and get back to you all.

---

