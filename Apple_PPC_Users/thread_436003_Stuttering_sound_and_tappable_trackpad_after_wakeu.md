---
title: "Stuttering sound and tappable trackpad after wakeup from sleep"
date: 2007-05-07
forum: Apple PPC Users
---

### Post by seebol on 2007-05-07
After I wake the computer up for sleep, any video/audio that I play stutters for a while, then after a few songs, it sometimes returns to normal; sometimes it'll continue to stutter hours later. Also, after the computer wakes up for sleep, the synaptic touchpad, which I configured to not register a click when I tap it, is tappable. I have an ibook g4 from July 2004. Any suggestions?

---

### Post by stmiller on 2007-05-07
What version of Ubuntu are you using? Have you tried the latest version (Feisty?)

---

### Post by seebol on 2007-05-07
This was a problem on the previous version of Ubuntu (6.10), and it's still a problem on the current version (Feisty).

---

### Post by stmiller on 2007-05-07
Very interesting. Not a problem on my G4 Tibook. Hardware and drivers are basically identical.

There is a specific sleep/wake script that ubuntu runs to tell specific things to unload/load when the machine is put to sleep or waken up. (Including network, sound, video, etc.) You can possibly edit these scripts. I'll have to hunt down their exact location.

---

### Post by gpi on 2007-05-08
Hello all !

I also have problem after wake up. I'm using Feisty Fawn on an iBook G3 500 MHz (the first white iBook, dual USB). After wake up, the screen remains black, completely black ! In which direction I have to look for ?
Thank you...

gpiroux

---

### Post by stmiller on 2007-05-08
Do you have these things installed:

sudo apt-get install pbbuttonsd powerpc-utils powernowd powermgmt-base

---

### Post by seebol on 2007-05-08
Yes, I have all of those installed and up-to-date. I should also mention that I have powerprefs installed, and when I run it after waking up, my trackpad is shown as "notap" even though it is tappable. Resetting this configuration doesn't do anything. The only remedy I've found is to restart.

---

### Post by ssam on 2007-05-08
try making a file called
```
/etc/apm/resume.d/90-trackpad
```

containing

```

#!/bin/bash
trackpad notap

```

and make it executable with

```

sudo chmod u+x /etc/apm/resume.d/90-trackpad

```

---

### Post by seebol on 2007-05-08
Should I create those directories if they don't exist already?

---

