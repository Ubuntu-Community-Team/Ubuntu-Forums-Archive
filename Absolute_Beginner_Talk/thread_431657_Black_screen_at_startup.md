---
title: "Black screen at startup"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by admsh on 2007-05-03
okay, i realise there's a lot of talk about this on the forum but i can't seem to find a solution searching, and it sounds like some people actually got it to work -
i have a dell inspiron 2500, with 256 megs of ram. i downloaded the latest version of ubuntu, burned the live CD and tried re-booting from it. i see the ubuntu logo with a first screen and menu, but when i try to start ubuntu i just get a black screen. nothing. i tried botting in safe graphics mode, but same thing. it says loading linux kernel and then everything disappears.
i saw somewhere you can press ctrl+alt+1 and get to a command line, so i did that and got there, but i have no idea what to do next, if anything, so that doesn't help me.

any idea of what this might be or what i can do to solve this issue? i understand this computer came with intel video card, or intel video on the motherboard, or something of that sort, and that this may be a video card issue?

any help would be really REALLY appreciated... i'm dying to move to linux finally...

---

### Post by dergringo on 2007-05-03
Hi

First of all verify that your cd's allright. Boot from the CD and in the menu choose "Check CD for defects". If no defects are reported we'll have a closer look.

greetings

Philipp

---

### Post by admsh on 2007-05-03
yeah cd is okay. and i've seen other posts of people with the same kind of problem, all have dell computers, most of the inspiron brand. it sounds like something with the graphics card, i just have no idea how to approach this.

---

### Post by 3rdalbum on 2007-05-03
Firstly:

At the menu where it says "Start or install Ubuntu" and the safe graphics option, press F1 and have a look through the help pages. They give you parameters and examples for different settings that may make problematic screens work.

If they don't help, then switch to the terminal in the way you described, then put in:

```
sudo dpkg-reconfigure xserver-xorg
```

You can usually accept the defaults that the program gives you, but when it asks you if you want to autodetect the video card, say No. Choose the "vesa" driver. Keep the defaults for all other settings, until you reach the end of the program and are brought back to the command-line.

Now type:
```

sudo -s
killall Xorg && /etc/init.d/gdm restart

```

Hopefully this should get everything working, albeit with unaccelerated graphics.

---

### Post by admsh on 2007-05-03
thanks... i'll give this a try later today.
is there any way to get accelerated graphics to work after all is installed, or do i need drivers from dell to do that?
i'm not sure it would be smart to move to ubuntu with this machine if i can only get it working this way...

---

### Post by admsh on 2007-05-03
i tried putting in the code, but i enter it, press enter and it just goes to the next line, nothing is happening.

i can't even check the CD, when i choose that option the "loading linux kernel" message comes up, then please wait, then nothing... blank screen again... i did notice it is trying to read from the floppy because the light comes up for a second.

what a miserable experience... i was hoping to get rid of windows altogether... does anyone have any ideas as to why this is happening?

---

### Post by bobplano on 2007-05-03
well it seems ubuntu just doesn't have the drivers for your card. why don't you post it here

---

### Post by admsh on 2007-05-03
well, in windows, under system info -> Display adapters, it says:
Intel(R) 82815 Graphics Controller

---

