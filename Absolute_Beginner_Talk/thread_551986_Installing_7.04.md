---
title: "Installing 7.04"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Jookia on 2007-09-15
Alright guys, I downloaded Ubuntu 7.04 last night.

Stuff I'm concerned about:

**Drivers**

Dual Core CPU
ADI 1986A Soundcard
ATi Radeon 9000

Stuff I'm wondering how I can run:

**Games**

CounterStrike: Source
Garry's Mod

**Programs**

Notepad

---

### Post by oilchangeguy on 2007-09-15
> **Jookia said:**
> Alright guys, I downloaded Ubuntu 7.04 last night.

Stuff I'm concerned about:

**Drivers**

Dual Core CPU
ADI 1986A Soundcard
ATi Radeon 9000

Stuff I'm wondering how I can run:

**Games**

CounterStrike: Source
Garry's Mod

**Programs**

Notepad

drivers
run the live cd, and go from there.

games
unless these are written for linux, i'd dual boot.

programs
not sure of another choice, probably is one.

---

### Post by splintercellguy on 2007-09-15
I'm a bit wary of your ATI card (perhaps the latest ATI binary might be ok), but other than that, LiveCD to see if it works. You'll probably want to use Wine to install, AppDb guide here: [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554) and latest Wine version from [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Ubuntu has many GUI text editors, but if you really want THE Windows Notepad, Wine has an implementation.

---

### Post by Dr Small on 2007-09-15
You should find Gedit much more facinating over the default windows notepad, and about the games. If you want to play the games, and they are not compatible with Linux (meaning they don't work period or don't have a clone), than your best bet would be to either, A.) Dualboot or B.) Install Windows in VirtualBox and run them in it.

That saves dualbooting.

Dr Small

---

### Post by Maestro23 on 2007-09-15
For your games, you can run some of the in Wine or get Cedega.

[http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by andymushu on 2007-09-15
as for the games, i have successfully played day of defeat source (a game based on counterstrike source) in feisty through wine. check out winehq.com to get more info on it. basically it emulates a windows environment on your linux OS, very useful for games. CS:S is among the best working games under wine. just make sure you get the accelerated drivers for your video card (xgl for ati, glx for nvidia), and you should be good to go.

---

### Post by Jookia on 2007-09-15
Alright, I'm deciding to go there but I'm looking to backup all my data to transport to Ubuntu (steam games etc). Does Ubuntu read DVD partitions made by windows?

---

### Post by st33med on 2007-09-15
Wine does a good job with the Steam app. You just need to get the correct text format.

---

