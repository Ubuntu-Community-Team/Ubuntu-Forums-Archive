---
title: "Ubuntu Is Too Laggy"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by MOkAONE on 2007-04-10
i recently installed Ubuntu Edgy (dual booting ubuntu / winXP), i have been around the boards for a bit but to be honest, ive lost some interested in linux due to the fact that its real lagy. theres always talk about people installing linux on old, slow computers because they run smoother than with windows.. so im assuming theres something wrong here.

i didn a little search did wat it sais on this thread [**click here**]("http://ubuntuforums.org/showthread.php?t=400425"), hopefully it helps people help me fix this problem.

lspci | grep VGA
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 96 00]

```

less /var/log/Xorg.0.log | grep LoadModule
> (II) LoadModule: "bitmap"
(II) LoadModule: "pcidata"
(II) LoadModule: "i2c"
(II) LoadModule: "bitmap"
(II) LoadModule: "ddc"
(II) LoadModule: "dri"
(II) LoadModule: "drm"
(II) LoadModule: "extmod"
(II) LoadModule: "freetype"
(II) LoadModule: "glx"
(II) LoadModule: "GLcore"
(II) LoadModule: "int10"
(II) LoadModule: "type1"
(II) LoadModule: "vbe"
(II) LoadModule: "ati"
(II) LoadModule: "kbd"
(II) LoadModule: "mouse"
(II) LoadModule: "wacom"
(II) LoadModule: "radeon"
(II) LoadModule: "vgahw"
(II) LoadModule: "int10"
(II) LoadModule: "shadowfb"
(II) LoadModule: "ddc"
(II) LoadModule: "i2c"
(II) LoadModule: "fb"
(II) LoadModule: "ramdac"
(II) LoadModule: "xaa"
(II) LoadModule: "theatre_detect"

hdparm -d /dev/hda
> /dev/hda: No such file or directory



top -i -n1
> 
top - 02:55:44 up 18 min,  2 users,  load average: 0.29, 0.31, 0.25
Tasks:  87 total,   1 running,  86 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.3% us,  1.4% sy,  0.1% ni, 84.0% id,  4.1% wa,  0.0% hi,  0.0% si
Mem:   1296188k total,   398644k used,   897544k free,    58444k buffers
Swap:   530136k total,        0k used,   530136k free,   176704k cached

  PID       USER       PR    NI  VIRT   RES    SHR  S  %CPU %MEM    TIME+  COMMAND
 5796   mokaone   15    0  2192  1004  768   R   0.0        0.1   0:00.01    top

---

### Post by justleen on 2007-04-10
what is it that your after, exactky?
did the above work for you?
What systems specs do you have?
What version of ubuntu are you running?

---

### Post by igknighted on 2007-04-10
Fairly common issue, luckily with an easy answer... you need to install drivers for your graphics card.  You can do that from synaptic (system->admin->synaptic) or the terminal (applications->accessories->terminal).  Because its easier to do over the forum, I am going to tell you the CLI way, but if you want to use synaptic just search for fglrx.

first, open the terminal.  Then run these three commands:
```
sudo apt-get update
```
```
sudo apt-get install xorg-driver-fglrx
```
```
sudo ati-config --initial
```

Then reboot, and your graphics issues should be gone.  Run this last command in the terminal after reboot to double check that all is well:
```
glxinfo | grep direct
```
and if it returns the direct rendering is enabled then everything is AOK.

---

### Post by MOkAONE on 2007-04-10
> **justleen said:**
> what is it that your after, exactky?
did the above work for you?
What systems specs do you have?
What version of ubuntu are you running?
-not sure wat u mean by the first two questions
-amd64 3700+. 1.25GB Ram, ATi Radeon 9600 Pro
-version 6.061 LTS

*in process of doing wat igknighted suggested*
**edit:** got stuck at "sudo ati-config --initial" it sais...
```
sudo: ati-config: command not found

```


but i thought i had already installed my video card drivers.. using Envy. that was the first thing i sais cuz i had read that having the right video card drivers helps out alot, sorry i forgot to mention that.

---

### Post by igknighted on 2007-04-10
next time it gets slow, open a terminal and run the command "top".  Report back what the top processes that are eating resources are please.  Also, can you give the results of ```
cat /etc/X11/xorg.conf
``` and ```
glxinfo | grep direct
```

---

### Post by Bloch on 2007-04-10
Many users including myself find the gnome GUI is less responsive than a clean windows installation. What I mean is, moving windows leaves "stepped tracks", resizing is less smooth etc. This might be what you mean by "laggy" which can happen even when the application itself works faster than on windows.

Nothing can compare to the absolute solidity of moving a window around the screen on OS X even on an old G3 blue imac 350MHz - far better than linux (or windows XP) on a 2.4GHz pentium with graphics card.

So - once you are sure your drivers are working - you might have to get used to a small lack in responsiveness, (I mean with gnome) but with greater speed for running several apps at once.

Here are some users' experiences.
[http://www.omgili.com/preview/aHR0cDovL3d3dy5uZW93aW4ubmV0L2ZvcnVtL2luZGV4LnBocD9zaG93dG9waWM9NDI4ODk1](http://www.omgili.com/preview/aHR0cDovL3d3dy5uZW93aW4ubmV0L2ZvcnVtL2luZGV4LnBocD9zaG93dG9waWM9NDI4ODk1)

---

### Post by mcduck on 2007-04-10
> **MOkAONE said:**
> -not sure wat u mean by the first two questions
-amd64 3700+. 1.25GB Ram, ATi Radeon 9600 Pro
-version 6.061 LTS

*in process of doing wat igknighted suggested*
**edit:** got stuck at "sudo ati-config --initial" it sais...
```
sudo: ati-config: command not found

```


but i thought i had already installed my video card drivers.. using Envy. that was the first thing i sais cuz i had read that having the right video card drivers helps out alot, sorry i forgot to mention that.

It's "sudo aticonfig --initial".. ;)

---

