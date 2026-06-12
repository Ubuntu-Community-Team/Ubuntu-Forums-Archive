---
title: "Enabling mouse wheel in 6.10 under Virtual PC"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by kopo88 on 2006-11-19
I'm currently running 6.10 under Microsoft Virtual PC, and I really miss being able to scroll with my mousewheel :). Is there any way to enable the wheel (or is this a limitation of Virtual PC?)?
I'm using a Logitech optical USB mouse.

Also, is there any way to add 1280x1024 as an allowed screen resolution in the same setup? Currently, 1024x768 is the maximum.

---

### Post by turbojugend_gr on 2006-11-19
ATTENTION: I 've never used MS virtual PC.

In a regular ubuntu session, you would have to open the /etc/X11/xorg.conf file with a text editor, and in mouse section add this line **Option         "ZAxisMapping" "4 5"** save and restart X.

Make sure you have backupped your initial xorg.conf file before doing this.

Try this it should work under a virtual machine too.

EDIT: After this edit the mouse section should look like:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

---

### Post by AnimalMother on 2006-11-26
> 
ATTENTION: I 've never used MS virtual PC.

In a regular ubuntu session, you would have to open the /etc/X11/xorg.conf file with a text editor, and in mouse section add this line Option "ZAxisMapping" "4 5" save and restart X.

Make sure you have backupped your initial xorg.conf file before doing this.

Try this it should work under a virtual machine too.

EDIT: After this edit the mouse section should look like:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection


I am using Virtual PC on winXP pro with Ubuntu 6.10 also.  I went to go try the above and the ZAxisMapping bit was already in there.  I tried a bunch of other stuff also to no avail.  I was using DamnSmallLinux and I could switch screen resolution and I had the scroll wheel working so I know it does work, so what is it about Ubuntu 6.10 that keeps this from working properly?  

Any Xorg gurus out there?

Thank you for your time.

---

### Post by graficus on 2006-12-18
Please post or PM me if you find a solution. 
This whole ordeal makes me want to abandon this linux adventure altogether.

---

### Post by puccaso on 2007-02-20
well
guess this
i cant even use my mouse!!!

i use virtual pc 2007

---

### Post by saviles on 2007-03-08
I've tried several setting changes in the xorg.conf file but none of enables the scroll wheel in VPC 2007. I restarted X and I restarted the system after i made a change and didn't work either.

Here are the other settings I tried

     Option          "Protocol"              "ImPS/2"
     Option          "ZAxisMapping"          "6 7"

I did find a [MSDN blog]("http://blogs.msdn.com/virtual_pc_guy/archive/2005/08/25/454850.aspx") post that talked about enabling the 4th and 5th button on a mouse, but its obviously for a windows system.

Anyone get this to work yet?

---

### Post by lobster on 2007-03-25
Hey
I'm running VMware, and also had problem with mouse wheel.

I had written in xorg.conf

Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"

but solution was to rewrite:
Option "Protocol" "PS/2"
to:
Option "Protocol" "ExplorerPS/2"

and restart xserver using CTRL+ALT+BACKSPACE

hope it'll help to u as well

---

### Post by saviles on 2007-04-02
I have the same thing setup in my xorg.conf file

```

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
EndSection

```

I haven't researched it much lately but I don't think its possible. Could you post what your Section looks like, if it differs from mine?

---

### Post by SmithAtlanta on 2007-04-11
This is happening in fedora core 7 also so I'm wondering if its a new x issue...

---

### Post by saviles on 2007-04-12
I'm quite sure its the way Virtual PC handles the X environment.

---

### Post by pavpan on 2007-04-24
Hey, I need help with changing the monitor resolution. I accidentally enabled 640x480 as the only monitor size, and now I want it to be 800x600 or 1024x7.. How do I change it?

---

### Post by pblanton on 2007-07-10
This worked for me in Feisty Fawn. I am running Feisty Fawn in VMWare 5.5.4 and the mouse wheel was not working. I made the following changes and forced a restart of X (ctrl-alt-Backspace) and voila!

```

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
EndSection

```

---

### Post by ashosborne on 2008-02-15
Hi,

one hint that worked for me to get the mouse wheel working in Virtual PC for Ubuntu 7.10 was adding the following line to 
/etc/modprobe.d/options 

```
options pmouse=imps
```

Greets
Ash

---

