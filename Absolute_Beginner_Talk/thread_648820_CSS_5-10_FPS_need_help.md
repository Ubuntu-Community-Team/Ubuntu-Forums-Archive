---
title: "CSS 5-10 FPS need help"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Wickedman on 2007-12-24
Hi, I have a big problem, I installed steam and CS:S and had no problems at all. (Used wine for emulator)
When I load CS:S and get into game I'm getting around 5-10 FPS and I don't know how to fix it.
I've searched and searched for a solution and tried the:  
```
cd /home/USER/.wine/drive_c/Program\ Files/Steam
WINEDEBUG="fixme-all" wine steam.exe
```
but it didn't help at all.

I've got the Nvidia 6200 SE graphics card with a 3.0 P4 CPU HT and 1gig of ram. (using nvidia-glx-new drivers)

With windows i got 70+ FPS but now 5-10 FPS i can't even play.

need help please :D

Thanks in advance

---

### Post by Rocket2DMn on 2007-12-24
Are you running Compiz-Fusion?  If so, you need to turn it off by running
```
metacity --replace
```
to enable CF after you're finished, just run
```
compiz --replace
```
I use this when I play cs 1.6, and just made links on my top panel (right click - > Add to Panel -> Custom Application Launcher and place those commands in the Command part).

---

### Post by Wickedman on 2007-12-24
> **Rocket2DMn said:**
> Are you running Compiz-Fusion?  If so, you need to turn it off by running
```
metacity --replace
```
to enable CF after you're finished, just run
```
compiz --replace
```
I use this when I play cs 1.6, and just made links on my top panel (right click - > Add to Panel -> Custom Application Launcher and place those commands in the Command part).

Tried what you said in Terminal it just said:
```
"Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager."
```
know how to fix it? :)

P.S I think i'm using Compiz-Emerald (if thats a version) i'm new to this, only installed Ubuntu yesterday.

---

### Post by Rocket2DMn on 2007-12-24
Can you post the exact output of the command line including the command you issued.  You may also need to adjust some NVIDIA settings from their configuration using
```
gksudo nvidia-settings
```
I'm not an nvidia guy (unfortunately b/c ati isn't so great with linux).  You may see something there like graphics acceleration which should be enabled.

Also, you need to make sure your nvidia drivers are enabled, according to you need to [http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new) run
```
sudo nvidia-glx-config enable
```

You can also check System->Administration->Screen and Graphics and hit the Graphics Card tab.

---

### Post by Wickedman on 2007-12-24
```
wickedman@wickedman-desktop:~$ metacity - - replace
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```

and in ```
gksudo nvidia-settings
``` everything looked ok.

---

### Post by Rocket2DMn on 2007-12-24
Hehe, this is why I asked for that info: you typed it in wrong - there is no space between the dashes, you can copy and paste this into the terminal (or to the Command part of Add to Panel -> Custom Application Launcher)
```
metacity --replace
```
and
```
compiz --replace
```
When metacity is enabled, the screen will flash and you won't have a desktop cube anymore with no fun little eyecandy.  You can re-enable compiz with the second command.  Use metacity when you play CS:S.

---

### Post by tomcheng76 on 2007-12-24
> winecfg
in Voice tab , choose OSS (NOT ALSA)
it may help

---

### Post by Rocket2DMn on 2007-12-24
> **tomcheng76 said:**
> in Voice tab , choose OSS (NOT ALSA)
it may help

This is a common solution to freezing, not sure it helps speed at all though.
I'll check up on this thread in the morning, I'm hittin' the sack.  Good night and good luck.

---

### Post by Wickedman on 2007-12-24
ok thanks for all the info, got me upto 17-19 FPS now :) know any other fixes or anything else i could be doing wrong? It's still kind of laggy :(

---

### Post by Wickedman on 2007-12-24
bump - messed around with files and terminal abit can't get anything to work now when I launch C:SS it just goes back to windows and nothing happens and same thing with Anarchy Online.

Tryed typing ```
gksudo nvidia-settings
```
into Terminal and it comes up with the error: 
```
You do not appear to be using the Nvidia X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

anyone got any clue how to fix this?

---

### Post by tomcheng76 on 2007-12-24
try
> sudo nvidia-xconfig
then
logout and ctrl+alt+backspace

---

### Post by Wickedman on 2007-12-24
tried it, still doesn't work and now my sounds gone too :( 
```
No volume control GStreamer plugins and/or devices found.
```
Checked on Synaptic Package Manager and everything what I had installed to get it working before is still there..

---

### Post by Wickedman on 2007-12-24
bump

---

### Post by Rocket2DMn on 2007-12-24
Check System->Preferences->Sound and be sure you can run sound through a music player or something.  Then check winecfg - if OSS doesn't cut it, you may need to use ALSA.

---

### Post by Wickedman on 2007-12-24
There's no default mixer available now, before their were two on there.
I can't choose any in ```
winecfg
```

Any ideas

---

### Post by Rocket2DMn on 2007-12-24
I don't understand what you mean exactly.  You have no choices for sound under Preferences or winecfg?
You need to work on getting sound to work through Ubuntu, then you can worry about wine.  Under winecfg->Audio you should have choices for Sound Drivers like ALSA and OSS.  Otherwise you may need to reinstall either the sound drivers or wine.

---

### Post by Wickedman on 2007-12-24
fix sound and everything loads now, just wondering how to get more FPS now, any ideas anyone? :D

---

### Post by Rocket2DMn on 2007-12-24
Depending on your computer specs, you may just be limited.  CS:S takes a lot more power than 1.6 and you will of course see some loss from windows since the game is essentially being emulated under wine (Wine Is Not an Emulator...).  You really just have to close down as much as possible, esp. compiz fusion.

---

### Post by tomcheng76 on 2007-12-24
did you choose OpenGL inside Video Setting of CSS ?

btw, i dont have CSS, i just have 1.6
my gf4 mx400 got 4-5x fps in 1.6 :)

---

