---
title: "ALSA is unstable"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by andy_blah on 2008-03-19
ALSA is very unstable sometimes so that at a random times it simply freezes the OS (I cannot even move the mouse cursor) or it both freezes the OS and it keeps looping 1-2 sec of the sound, leaving me with no other option that to hardware-reset the PC. Also when I use a midi software player (like Timidity or KMid) it freezes the OS.
Is there a possible fix for this, or should I update ALSA? Is my computer too slow? Is my soundcard the fault?

My specifications:
Intel P4 Celeron D (I know, I know) @ 2.26GHz
376MB RAM
VIA AC'97 on board (V8237) + CMI 8738MC6 (the soundcard that I set as default in asoundconf and witch I use)
Ubuntu 7.10 "Gutsy Gibbon"

Thank-you in advance,
>-Andy-<

---

### Post by kerry_s on 2008-03-19
so you got 2 sound cards?

try running the alsa config thing and select it there.
**sudo alsaconf**

then reboot, to make sure, other modules are unloaded.

---

### Post by andy_blah on 2008-03-19
Command not found.

---

### Post by kerry_s on 2008-03-19
> **andy_blah said:**
> Command not found.

then you do not have alsa.
sudo apt-get install alsa-base alsa-utils

---

### Post by andy_blah on 2008-03-19
If I did not have ALSA, how could I get sound then?
The result of the command:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.

```

---

### Post by kerry_s on 2008-03-19
you might have been using esound instead.

anyways, the command is correct did you use sudo?

if so you should fully uninstall alsa and reinstall it back, then try the->
sudo alsaconf

again

---

### Post by andy_blah on 2008-03-19
I am absolutely positive that I used the correct command:
```
andy@andy:~$ sudo alsaconf
[sudo] password for andy:
sudo: alsaconf: command not found
andy@andy:~$ 

```
And that I was using ALSA in the playback and ALSA is the default. I will try to reinstall it and I will edit this post so check often please.

EDIT 
------
Result:
```
andy@andy:~$ sudo apt-get purge alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
The following packages will be REMOVED:
  alsa-base* ubuntu-minimal*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 418kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 94637 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing alsa-base ...
Purging configuration files for alsa-base ...
Remaking /dev/sndstat.

andy@andy:~$ sudo apt-get install alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
Suggested packages:
  alsa-oss
The following NEW packages will be installed:
  alsa-base
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 182kB of archives.
After unpacking 369kB of additional disk space will be used.
Get:1 http://ro.archive.ubuntu.com gutsy/main alsa-base 1.0.14-1ubuntu2 [182kB]
Fetched 182kB in 0s (433kB/s)
Selecting previously deselected package alsa-base.
(Reading database ... 94597 files and directories currently installed.)
Unpacking alsa-base (from .../alsa-base_1.0.14-1ubuntu2_all.deb) ...
Setting up alsa-base (1.0.14-1ubuntu2) ...

andy@andy:~$ sudo alsaconf
sudo: alsaconf: command not found
andy@andy:~$ 

```

---

### Post by kerry_s on 2008-03-19
can you try uninstalling in synaptic please, make sure you get all the alsa marked for complete removal. your output says it only did the base.

---

### Post by andy_blah on 2008-03-19
See this screencast:
[[IMG]http://images.cdmazika.com/images/05qk62tisznasy3gnc09_thumb.gif[/IMG]](http://images.cdmazika.com/viewer.php?file=05qk62tisznasy3gnc09.gif)

---

### Post by kerry_s on 2008-03-19
okay, the only thing i can think of is it's a permissions thing.
try this->
[B]sudo -i
alsaconf[/B]

ps: love that screencast thing :)

anyway's if that don't work i'm all out of ideas. :(

---

### Post by Oldsoldier2003 on 2008-03-19
perhaps he meant alsactl ? take a look at this thread you may find some solutions
  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by andy_blah on 2008-03-19
Same result:
```
andy@andy:~$ sudo -i
[sudo] password for andy:
root@andy:~# alsaconf
-bash: alsaconf: command not found
root@andy:~# 

```

You can do screencasts by installing Byzanz:
```
sudo apt-get install byzanz
``` 

And the usage info(if you prefer using the terminal):
```
byzanz-record --help
```

Or right-click on one of the GNOME panels (witch I did not see in your screenshot) and select Add To Panel, after that select Desktop Recorder.

kerry_s, thank-you so far for your help.

---

### Post by andy_blah on 2008-03-19
Oldsoldier2003, my soundcard works, there is sound, just that ALSA sometimes makes the OS freeze

Sorry for double posting

---

### Post by Oldsoldier2003 on 2008-03-19
> **andy_blah said:**
> Oldsoldier2003, my soundcard works, there is sound, just that ALSA sometimes makes the OS freeze

Sorry for double posting

yeah that thread is a compilation of lots of little fixes and some big ones as well. some things that come to mind would be to check your settings for the sound card and perhaps install the latest alsa drivers from source. some cards are trickier than others to get working correctly.

---

### Post by kerry_s on 2008-03-19
> **andy_blah said:**
> Same result:
```
andy@andy:~$ sudo -i
[sudo] password for andy:
root@andy:~# alsaconf
-bash: alsaconf: command not found
root@andy:~# 

```

You can do screencasts by installing Byzanz:
```
sudo apt-get install byzanz
``` 

And the usage info(if you prefer using the terminal):
```
byzanz-record --help
```

Or right-click on one of the GNOME panels (witch I did not see in your screenshot) and select Add To Panel, after that select Desktop Recorder.

kerry_s, thank-you so far for your help.


thanks, i know how to do it, i use to use xvidcap on my desktop way back before it died. this current laptop don't got enough power for that, 450mhz, 256mb ram, 2.5mb vid, i got like 2 frames a second the last time i tried, then it just hard locked. :(

anyway's, sorry i was of no help, i hope you figure it out. take care.

---

