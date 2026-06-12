---
title: "Shell script?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by .Maleficus. on 2006-06-27
I am having trouble launching a few games.  They are Sauerbraten and UFO: Alien Invasion.  When I click on what I think is the icon to launch it, nothing happens.  These files happen to be "Shell scripts".  What is a Shell script?  How do I run it?  Do I need to add more files to the shell script, or am I just clicking the wrong thing?

P.S.  I used Loki installers to get the games.

---

### Post by skale on 2006-06-27
A shell script is basically a set of commands, if I wanted to run "asdfg" I'd type:
> sudo sh asdfg

---

### Post by .Maleficus. on 2006-06-27
I tried this, is it right?  Because nothing happened.

```
andy@andy-desktop:~$ sudo sh ufoai
Password:
ufoai: ufoai: is a directory
andy@andy-desktop:~$
```

Is that how I am supposed to launch the game?

---

### Post by Solver on 2006-06-27
In your example, ufoai is a directory. Therefore, you would first need to execute

```

cd ufoai
```

and then run sudo sh filename, where filename is the script's name. It might also be ufoai.

---

### Post by .Maleficus. on 2006-06-27
Does this mean something to anyone?

```
andy@andy-desktop:~$ cd ufoai
andy@andy-desktop:~/ufoai$ sudo sh ufoai
Adding game dir: ./base
using /home/andy/.ufoai/base/ for writing
Adding game dir: /home/andy/.ufoai/base
execing default.cfg
couldn't exec config.cfg
execing keys.cfg
Console initialized.

------- sound initialization -------
Using Alsa
Using sounddevice "default" - if you have problems with this try to set the cvar snddevice to a appropriate alsa-devicesound sampling rate: 48000
------------------------------------
------- Loading ref_glx.so -------
LoadLibrary("ref_glx.so"): can't open /etc/ufo.conf - setting search path to .
LoadLibrary("ref_glx.so") failed: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
Dumped console text to /home/andy/.ufoai/base/gl_debug.txt.
recursive shutdown
Error: Couldn't initialize OpenGL renderer!
Consult gl_debug.txt for further information.
andy@andy-desktop:~/ufoai$
```

I have an nvidia card, with all the drivers updated, so why can't it initialize the OpenGL renderer?

---

### Post by Solver on 2006-06-27
I would hazard a guess at you not having the SDL library installed. The file that your game is complaining about is in the libsdl-ttf-2.0-0 package. So you want to install that package through Synaptic or the terminal. The easiest way is just to

```

sudo apt-get install libsdl-ttf-2.0-0
```

(or just open Synaptic, type lidbsdl-ttf in the find dialogue and install the package)

---

### Post by .Maleficus. on 2006-06-27
```
andy@andy-desktop:~$ sudo apt-get install libsdl-ttf-2.0-0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libsdl-ttf-2.0-0
andy@andy-desktop:~$
```

I went into Synaptic and searched for that package, and got nothing.

---

### Post by Solver on 2006-06-27
Have you tried searching for simply "libsdl-ttf" in Synaptic? I might have a different name for some weird reason.

Do you have the extra repositories enabled? If not, you should add the universe and multiverse ones:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

