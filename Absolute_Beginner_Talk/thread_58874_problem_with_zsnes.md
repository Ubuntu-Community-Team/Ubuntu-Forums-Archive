---
title: "problem with zsnes"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-08-21
I just installed zsnes by using the commands
wget [http://sethkinast.com/ubuntu/hoary/backports/zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb)

sudo dpkg -i zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb 

when I run a game in zsnes, the game works but there is no audio.  I also noticed that it said "sound int failed" on the command line.  How can I fix this problem?

This was the output that I received from my command line.



ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.
Please report crashes to [email]zsnes-devel@lists.sourceforge.net[/email].

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

Sound init failed!
freq: 32000, channels: 2, samples: 1024
ZSNES could not find any joysticks.

---

### Post by xethm55 on 2005-08-21
Does your system have sound normally?

If so, This could be due to having another application using sound, such as Totem or another game.  

-xethm55

---

### Post by racermike1967 on 2005-08-21
No nothing else is using my sound.  Did I install it right?

---

### Post by jyank on 2005-08-21
If sound works everywhere else, try typing this in a terminal before loading zsnes

```
killall esd
```

Some other sounds might not work after typing this (gaim is the one I use that I notice when typing it) but you can get it right back on by going in a terminal and typing 

```
esd
```

Not sure if this is the problem, but worth a try

---

### Post by racermike1967 on 2005-08-21
[QUOTE=jyank]If sound works everywhere else, try typing this in a terminal before loading zsnes

```
killall esd
```

Some other sounds might not work after typing this (gaim is the one I use that I notice when typing it) but you can get it right back on by going in a terminal and typing 

```
esd
```

Not sure if this is the problem, but worth a try[/QUOTE]
 What does this command do?  What is esd?

---

### Post by jyank on 2005-08-22
esd is an audio plugin, killing is pretty much shuts it off.

Sometimes ESD can interfere with other programs and cause issues, so by killing it, the issues are avoided ;)

---

### Post by TristanMike on 2005-08-22
[QUOTE=racermike1967]What does this command do?  What is esd?[/QUOTE]The command, well, it Kills, or ends, ESD which has to do with sound. For a good read about ESD, OSS, and ALSA, check out this thread.... [http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)

Hope this helps

---

