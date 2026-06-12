---
title: "zsnes not working"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Zzl1xndd on 2007-11-09
This is what I get when I try to use Zsnes

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/enigma/.kde/socket-enigma-desktop.
can't create mcop directory

anyone got any ideas?

---

### Post by Druke on 2007-11-11
getting same error

---

### Post by Fibonacci on 2007-11-12
Please post the contents of /etc/libao.conf

---

### Post by danran on 2007-11-21
I am also getting the same error.  

>>>
dan@SunsetFire:~$ cat /etc/libao.conf
default_driver=alsa09
<<<

>>>
dan@SunsetFire:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/dan/.kde/socket-SunsetFire.
can't create mcop directory
<<<

---

### Post by Fibonacci on 2007-11-21
> **danran said:**
> >>>
dan@SunsetFire:~$ cat /etc/libao.conf
default_driver=alsa09
<<<

Change it to default_driver=alsa and try again.

---

### Post by danran on 2007-11-21
I got it to work by running this from the terminal window:
>>>
zsnes -ad oss
<<<

---

### Post by Fibonacci on 2007-11-22
> **danran said:**
> I got it to work by running this from the terminal window:
>>>
zsnes -ad oss
<<<

And you also got software sound mixing to work while that is running? You might want to try "zsnes -ad alsa" instead if OSS gives you any problems with mixing.

---

