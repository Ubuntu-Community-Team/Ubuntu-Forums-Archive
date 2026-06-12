---
title: "Nvidia GeForce FX Go5200 Problem"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by devientartist on 2007-12-05
Hello, I'd first like to say that I'm a complete ubuntu idiot I just installed it yesterday and thats the first time I've even seen or heard of ubuntu. 

Heres my problem I have a Nvidia GeForce FX Go5200 in my Dell inspiron 8600. I installed Ubuntu with no problems but now it will not let me enable the video card driver it gives the the following error. 

[B]The Sofware source for the package

nvidia-glx-new

is not enabled. [/B]

I'm not sure what this means i've done some google searches and they have not really helped yet. I really appreciate any dummied down advice. 

Thanks

---

### Post by FuturePilot on 2007-12-05
Go System>Administration>Software Sources. Make sure all of the check boxes are checked in the first tab. Also uncheck the one for the CD-ROM if it happens to be checked. Go to the Updates tab and check the first two boxes. Optionally you can check the fourth one to enable the backports. Close the window and Reload the sources when prompted. Then try installing the driver again.

---

### Post by devientartist on 2007-12-05
Well that worked great!

Now I was trying to turn on desktop effects and it will not allow it. It doesn't give a specific error message it just says "Desktop effects could not be enabled" I'm assuming its possibly my graphics card won't support it? Any suggestions?

Thanks again!

---

### Post by FuturePilot on 2007-12-05
Can you run 
```
compiz --replace
```
in a terminal and post what it says

---

### Post by devientartist on 2007-12-05
I typed that into the terminal and this is what it returned. 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 248, IRQ 11
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

I'm assuming by the last line that it doesn't have enough memory? I guess I could order more, but If I do that I wonder if my processor could keep up. :confused:

Thanks for your info!

---

### Post by FuturePilot on 2007-12-05
Sort of. You don't have enough video memory or VRAM which is RAM that is on the graphics card. You could try running Compiz like this and see if it works
```
SKIP_CHECK=yes compiz
```

---

### Post by devientartist on 2007-12-05
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

I'm still getting this message. Its an older machine so I guess its to be expected. Thank you so much for you input!

---

### Post by FuturePilot on 2007-12-05
Hmmm. Looks like we might have to do it the hard way.
```
gksudo gedit /usr/bin/compiz
```
Find the section that looks like this
```
# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default
```
Change the "65536" to "30000" save then try
```
compiz --replace
```
You might get black windows though due to a bug in the driver. If you do try using indirect rendering
```
compiz --replace --loose-binding --indirect-rendering
```

---

### Post by devientartist on 2007-12-05
Thanks! It works perfectly now!

You da Man!

---

### Post by noelrocha on 2008-01-29
I have a Dell Latitude with the same Nvidia GeForce FX Go5200.

I could make it running but it is a lot slow. 

do you have any help?

thanks

---

### Post by devientartist on 2008-01-29
My does run slow, but its probly because it not technically fast enough.

---

### Post by nutbastard on 2008-01-29
devient, I have the same exact computer. tried to get compiz working, gave up and removed it. IF you decide to remove compiz, it will mess up your window manager unless you run

metacity --replace

minimize that terminal and open another

sudo aptitude autoremove compiz*

Make sure you run metacity --replace BEFORE removing compiz if you decide to do so.

I don't recomend removing it, it doesn't seem to hurt anything just sitting there, but since you said it was running slow, i figured uh oh, he might try to remove it. I know i did, and it's caused a lot fo headaches

If it gets messed up (no titlebars, no multiple desktops) then you can usually open a terminal and run the replace code.

Theres a thread that gets into this here:

[http://ubuntuforums.org/showthread.php?t=680819&highlight=nutbastard](http://ubuntuforums.org/showthread.php?t=680819&highlight=nutbastard)

I've been trying to find people with the same setup as we have in order to communicate about specific problems. Im pretty noobish too but im getting the swing of it. I can help you get divx and other stuff running if you need help with that (no how-to's i found did it right for this setup)

im at gmail. peace!

---

