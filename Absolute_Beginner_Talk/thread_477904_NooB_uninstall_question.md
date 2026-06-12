---
title: "NooB uninstall question"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Bittermormon on 2007-06-18
I have been playing around with trying to use SynCE to sync my PocketPC with Ubuntu. If I can pull this off I can pretty much abandon XP at home. I have been using [this]("http://ubuntuforums.org/showthread.php?t=30936&highlight=pocketpc") tutorial, but I think I screwed up when setting up SyncCE. 

So my question is how would I go about undoing everything I've done so i can re-setup synCE. Also can anyone point me to a good reference (either online or in print) that explains what all these commands are that I am typing. I am a total Linux Noob but Ubuntu has made it a pretty easy jump.

---

### Post by reset3x on 2007-06-18
Are you using a serial port or USB?

---

### Post by Bittermormon on 2007-06-18
I am using USB. I'd love to eventually use BT, but am trying to take it one step at a time.

---

### Post by reset3x on 2007-06-18
You could sudo apt-get remove the packages you installed ..... Did you try using multisync? Its in System/Preferences/Removable Drives and Media... I had good success with that and my Jornada....

---

### Post by scott_evil on 2007-06-18
See if you can use Synaptic to remove the packages. The 'Mark for complete removal' option should remove configuration files, too.
You can check out [this tutorial](http://www.ubuntugeek.com/pocket-pc-syncing-with-evolution-in-ubuntu.html) which gives a little more explanation about what the steps are.

---

### Post by Bittermormon on 2007-06-19
thanks gang I was able to use synaptic. I had no idea that even existed. I might just figure out Linux yet.

---

### Post by atria on 2007-06-19
Just for your information: You can remove packages using the commandline too.

```
aptitude purge <packagename>
```

to ensure a clean uninstallation (including the configuration files)

---

