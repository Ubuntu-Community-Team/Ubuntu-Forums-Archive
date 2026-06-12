---
title: "[SOLVED] WINE Problem"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by victor9098 on 2007-10-31
Hi Everyone,

Right, little problem with WINE...probably more me though! :confused:

I have been trying to install a new game, I "ch" to the drive, type "wine setup.exe" then nothing happens. First time this has happened, all the game specs are the same to previous games. 

Sometimes the cd drive spins, but no install screen appears. 

Any advice would be great, if you require any more information just ask!

Thank you

---

### Post by Dr Small on 2007-10-31
Depends upon if your cd is in cdrom0 or cdrom, but you could try this:
```
wine /media/cdrom0/setup.exe
```

---

### Post by victor9098 on 2007-11-01
Yes you are right.

I am cdrom0, but still no luck getting the setup.exe file to run. Other files will run when I try to access them (but fail since the game is not installed).

Other games have installed with few issues, just do not understand why the setup.exe fails to run! 

Thank you

---

### Post by skymera on 2007-11-01
what version of wine you uing?

i found 0.9.47 and 0.9.48 to be useless.

0.9.46 is mighty good

---

### Post by victor9098 on 2007-11-01
The version from the synaptic repos...0.9.46

Like I said, first time this has happened! Usually I just cd to the drive with terminal, then wine the setup.exe file, but nothing happens!

I had a look in the autorun file tried to run the files listed in it but no good, I need to do via setup I guess. :confused:

Thank you

---

### Post by Clickbg on 2007-11-01
Can you paste what wine says when execute the command wine setup.exe. Usually that`s the key.

---

### Post by victor9098 on 2007-11-01
> keith@keith-vaio:~$ cd /media/cdrom0/
keith@keith-vaio:/media/cdrom0$ wine setup.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
keith@keith-vaio:/media/cdrom0$ 


That is what I do! The warnings are not new and stuff usually runs!

---

### Post by victor9098 on 2007-11-01
Also, when I try to go around the setup file and install I get the following:

> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:imm:ImmGetDefaultIMEWnd (0x10028 - (nil) 0x120f18 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10028 - 0x1003e 0x120f18 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10028 - 0x1003e 0x120f18 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10028 - 0x1003e 0x120f18 ): semi-stub
keith@keith-vaio:/media/cdrom0$ 

:confused: What to do? :confused:

---

### Post by victor9098 on 2007-11-01
Right, I went to the WINE website. Upgraded to the latest version. Still nothing happened.

Tried installing WINE-DOORS but it would not detect my network connection.

Uninstalled all of the above.

Removed the hidden .wine & .wine-doors folders.

Reboot.

Went to Synaptic, reinstalled WINE.

Inserted the CD-ROM

Right clicked the setup.exe file one last time (was about to start a thread on how to set up a windows partition...)

Installation Started

:guitar:

Thank you for your help...I believe this is solved!

---

### Post by skymera on 2007-11-01
usuaklly deleting the config files from home solves problems :)

always in the home directory. :wink:

---

### Post by victor9098 on 2007-11-01
Now you tell me :lolflag:

Think I might have a new problem though: [http://ubuntuforums.org/showthread.php?t=599808](http://ubuntuforums.org/showthread.php?t=599808)

Thanks again!

---

