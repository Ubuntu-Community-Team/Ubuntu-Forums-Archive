---
title: "High CPU usage"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by 5ER on 2007-04-03
Everything is slow in my kubuntu installation. It works normally in kubuntu live cd and in winsux.
ksysmanager doesn't show anything consuming too much CPU. And all together should be fine too, but it isn't.
Any ideas?

---

### Post by Jovec on 2007-04-03
First we'll have to determine what part of the system is causing this slowdown.  The most common areas would be CPU, Video card, or hard drive related.  I'm not familure with KDE, but I can offer some advice at least:

Post the output of the following commands run from a terminal. (you'll need to be case sensitive):

```
lspci | grep VGA
less /var/log/Xorg.0.log | grep LoadModule:
hdparm -d /dev/hda
top -i -n1
```

*I don't remember if hdparm is installed by default.*

---

### Post by 5ER on 2007-04-04
Here are the outputs. Commands are outside the code tags and outputs are inside code tags.

lspci | grep VGA```
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
```
less /var/log/Xorg.0.log | grep LoadModule:```
(II) LoadModule: "bitmap"
(II) LoadModule: "pcidata"
(II) LoadModule: "i2c"
(II) LoadModule: "bitmap"
(II) LoadModule: "ddc"
(II) LoadModule: "extmod"
(II) LoadModule: "freetype"
(II) LoadModule: "glx"
(II) LoadModule: "int10"
(II) LoadModule: "type1"
(II) LoadModule: "vbe"
(II) LoadModule: "dri"
(II) LoadModule: "drm"
(II) LoadModule: "dbe"
(II) LoadModule: "nvidia"
(II) LoadModule: "kbd"
(II) LoadModule: "mouse"
(II) LoadModule: "wacom"
(II) LoadModule: "fb"
(II) LoadModule: "ramdac"
(II) LoadModule: "GLcore"
```
hdparm -d /dev/hda
```
/dev/hda: No such file or directory
```
hdparm -d /dev/sda```
/dev/sda: Permission denied
```
sudo hdparm -d /dev/sda```
/dev/sda:
```and then nothing
top -i -n1```

top - 10:34:02 up 18 min,  1 user,  load average: 0.00, 0.36, 0.53
Tasks:  89 total,   1 running,  88 sleeping,   0 stopped,   0 zombie
Cpu(s): 30.0%us,  7.7%sy,  0.0%ni, 57.9%id,  3.3%wa,  0.2%hi,  0.9%si,  0.0%st
Mem:   1542492k total,   652856k used,   889636k free,    17400k buffers
Swap:  1004052k total,        0k used,  1004052k free,   385296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
11250 peter     15   0 10632 1212  880 R  0.0  0.1   0:00.00 top

```

---

### Post by Jovec on 2007-04-04
For the Video subsystem, you need to remove the "dri" and "GLCore" modules from loading.  They aren't used with the proprietary nvidia driver, which is what you are using.

You can do this by hand by placing a # in front of the appropriate lines in the /etc/X11/xorg.conf file

```
sudo vim /etc/X11/xorg.conf
```

*repleace vim with your editor of choice, such as nano or appropriate GUI app.*

and change it to read

```

#Load "dri"
#Load "GLCore"

```

You'll have to reboot, or restart the X server (CTRL+ALT+Backspace, save your work first).


As for hdparm, it's really meant for IDE drives not Serial ATA which is most likely what you have.  I took a guess... we mainly wanted to see if DMA was enabled.


Top showed no running process grabbing up CPU.  Check again in ksysmanager, but look for an option to show all processes, not just yours.

Try the xorg.conf changes and see if it is any better for you.

---

### Post by 5ER on 2007-04-06
There are no >load "dri"< and >load "GLcore< in xorg.conf.

I have found out, that a game in winsux might also run slower than it should and sometimes this game starts to go very very slow, but this game is only thing where performance drop is visible. I have to reboot winsux then (I tried no other game).
But now, this happed in Linux once too, I had to reboot, because it was too slow.

So, maybe it's a hardware problem, but this problem didn't occur never before.
About high CPU, that doesn't happen anymore, maybe it was a coincidence.

I removed dust from computer, but it's the same.

---

### Post by kokiperex on 2007-04-21
Same problem here. I have a Pentium 4, 2.8GHz, 512MB RAM. Kubuntu 7.04 (but I have the problem from 6.10), nVIDIA GeForce3 Ti200.

```
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
```
```

less /var/log/Xorg.0.log | grep LoadModule:
(II) LoadModule: "pcidata"
(II) LoadModule: "i2c"
(II) LoadModule: "ddc"
(II) LoadModule: "extmod"
(II) LoadModule: "freetype"
(II) LoadModule: "int10"
(II) LoadModule: "vbe"
(II) LoadModule: "glx"
(II) LoadModule: "v4l"
(II) LoadModule: "nvidia"
(II) LoadModule: "kbd"
(II) LoadModule: "mouse"
(II) LoadModule: "wacom"
(II) LoadModule: "fb"
(II) LoadModule: "ramdac"
```

When my system is inactive, the Xorg CPU usage goes to 99%. I have to open a terminal session and kill it with kill -9.

Any idea?

---

### Post by Lucifiel on 2007-04-21
Why not trying running "top"  and see which processes are consuming memory?

---

### Post by kokiperex on 2007-04-21
> **Lucifiel said:**
> Why not trying running "top"  and see which processes are consuming memory?

It's the Xorg process. But only when the system is inactive for about 20 minutes (even if I don't use a screensaver).

---

