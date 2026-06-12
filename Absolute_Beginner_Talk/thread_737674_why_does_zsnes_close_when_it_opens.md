---
title: "why does zsnes close when it opens"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by timetoballj on 2008-03-27
as soon as i open zsnes it closes as fast as it opens

---

### Post by timetoballj on 2008-03-27
no one can help

---

### Post by jpeddicord on 2008-03-27
Could you run zsnes in a terminal (Applications > Accessories > Terminal)?

Just type the following line and hit Enter:
```
zsnes
```

Then highlight the error(s) you get, right-click and Copy, and then paste it here.

---

### Post by angry_johnnie on 2008-03-28
If you get some sort of "mcop" error, this thread might help you.

[http://ubuntuforums.org/showthread.php?t=593888](http://ubuntuforums.org/showthread.php?t=593888)

---

### Post by Ryan450 on 2008-03-29
I'm having the same issue, however I noticed this only started after I upped my desktop views to 4, and put in the cube rotate on my visual effects. Heres the terminal output.

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Segmentation fault (core dumped)

```

any ideas?

---

### Post by newagelink on 2008-04-14
In Ubuntu 7.04, I just turned my Appearance visual effects from the max setting to none ... no difference. zsnes still closes immediately after it opens for me, too. Apparently I'm also getting that mcop error:
```
daniel@daniel-laptop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/daniel/.kde/socket-daniel-laptop.
can't create mcop directory
```

---

### Post by newagelink on 2008-04-14
> **angry_johnnie said:**
> If you get some sort of "mcop" error, this thread might help you.

[http://ubuntuforums.org/showthread.php?t=593888](http://ubuntuforums.org/showthread.php?t=593888)Thanks! Awesome!
```
daniel@daniel-laptop:~$ sudo sh -c 'echo "default_driver=alsa" > /etc/libao.conf'
[sudo] password for daniel:
daniel@daniel-laptop:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.
daniel@daniel-laptop:~$
```

---

