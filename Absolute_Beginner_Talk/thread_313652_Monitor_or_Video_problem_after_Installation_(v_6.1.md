---
title: "Monitor or Video problem after Installation (v 6.10)"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by MayItBe on 2006-12-06
Hi,

I am a new linux and Ubuntu fan. I have just installed the 6.10 version at my school in the computer lab. Installation worked fine. When I rebooted after the install, and after linux started, the monitor's screen just showed me a simple floating box with this message (not the exact words): "resolution or refresh rate not compatible".
I managed after a reboot to enter in "safe mode" and I landed in the command line box from Ubuntu.
How can I fix or change the video resolution so it is compatible with the monitor ? What command line syntax should I use. Dare I say that I don't know anything about bash or other commands ...

Thanks for you help. If you need more details I can give them ASAP.

FH

---

### Post by geekygreen on 2006-12-06
When I installed Ubantu, I had the same problem.  I took the easy way out...I installed a more capable monitor, used the System/preferences/screen resolution to change the display to a 60 cycle refresh, then switched monitors again.

I am new enough to this to be unfamiliar with the command line stuff also...I find new command line stuff every day on the forum....I am still searching for a decent simple catalog of what is actually available!

---

### Post by bodhi.zazen on 2006-12-06
Start with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart X with:```
sudo gdm
```

---

### Post by deadgobby on 2006-12-06
Either you are at school taking a test to install a Linux program, you are trying to impress some one, or you are doing some that you shouldn't. 
Gobby
PS some one gave you the answer.

---

### Post by geekygreen on 2006-12-06
> **bodhi.zazen said:**
> Start with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart X with:```
sudo gdm
```

What keystroke combination is required to get to a terminal window, if you cant see the graphical environment in order to select a terminal session, because the monitor is not processing the data?:-k

---

### Post by MayItBe on 2006-12-06
> **bodhi.zazen said:**
> Start with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Restart X with:```
sudo gdm
```

Thank you for the answer! I'll try the command line you suggested (tomorrow) and let you know if it worked.

Thanks.

FH

---

### Post by bodhi.zazen on 2006-12-06
> **geekygreen said:**
> What keystroke combination is required to get to a terminal window, if you cant see the graphical environment in order to select a terminal session, because the monitor is not processing the data?:-k

Ctrl-Alt-F1

Ctrl-alt-F7 to return to you GUI

---

### Post by MayItBe on 2006-12-07
Hi,

I tried the command lines and it worked fine. Thank you again for your help.
FH

---

