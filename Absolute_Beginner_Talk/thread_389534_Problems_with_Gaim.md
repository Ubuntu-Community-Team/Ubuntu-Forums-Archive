---
title: "Problems with Gaim"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by bparham on 2007-03-20
When I booted my system this evening it told me that I had updates, so I allowed Update Manager to run, one of the updates was for Gaim. After installing I can no longer get Gaim to start. It takes approximately 30+ seconds to start. but then nothing. If I open System Monitor it says that the program is running, but I can't seem to get it to do anything. I've tried re-installing, even uninstalling and re-installing and nothing. Any ideas? Synoptic tells me that I'm running 1:2.0.0+beta6-1ubuntu2~dapper1

---

### Post by xopher on 2007-03-21
Try downgrading to the last version that worked to make sure the update is the cause of this.

```
sudo apt-get install gaim=1:2.0.0+beta6-1ubuntu2~dapper1
``` for the one you have installed now, just replace that with the previous version. Might need to use some force flag too.

---

### Post by bparham on 2007-03-21
Ok, perhaps i'm missing something, i have completely unistalled Gaim, I have tried the command line provided above, the program installs, but nothing. When I check system monitor it says that the program is sleeping. 

I have also tried to install from the source, however when I run ./configure I receive an error saying that I need GLib 2.0 despite the fact that I have a higher version. I would reinstall GLib, but I can't seem to find the actual program name to do so. 

Suggestions?

---

