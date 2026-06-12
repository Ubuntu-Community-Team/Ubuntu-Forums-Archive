---
title: "Need to format a 250GB SATA HD - Model WD2500JS"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by HighD on 2007-01-03
I need to format CLEAN a 250GB Sata HD, it's a western Digital model WD2500JS..The thing is WD provides a tool called Data LifeGuard Diagnostics which you can use to **WRITE ZEROS TO DISK**, and completely wipe/clean it...my question is..does anybody know a different way(to wype my HD clean) as it seems when I boot this tool (the one provided by WD), it does not recognize my drive..it gives me an error something like this..

[B]Caldera DR-DOS 7.5

ERROR: no cd rom drive found

ERROR: IDE cd rom device driver NOT installed

a:/>echo off 

driver not found : 'generic'

a:/> NWCDEX.exe requires a Driver name to be specified

Invalid drive specified


command or filename not specified

command or filename not specified

command or filename not specified

command or filename not specified
[/B]


well, that's the output..if anyone knows a fix to this (it seems it aint recognizing my SATA DRIVE)..please let me know or IF ANYONE KNOW ANOTHER SAFE WAY TO WIPE MY HD CLEAN please let me know also..

thanks in advance for all your help :mrgreen:

---

### Post by BarfBag on 2007-01-03
I don't understand your problem, but have you tried GParted?  It's in the repos.

---

### Post by HighD on 2007-01-03
I just need to wipe my HD clean, to start from scratch and install ubuntu and windows again. I have used gparted but I dont think i can use it to format it clean, i need some bootable stuff...:-k

---

### Post by HighD on 2007-04-02
Anyways I ended up just reformatting with Windows installer, installed both systems to dual boot (xp and ubuntu) and everything is fine :D

About the problem, I found out that the software had some bugs, something to do with SATA I think. Don't know why but everything works great now :mrgreen:

---

