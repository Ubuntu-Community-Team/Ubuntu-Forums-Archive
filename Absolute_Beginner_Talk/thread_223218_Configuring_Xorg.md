---
title: "Configuring Xorg"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Crypty on 2006-07-26
Hi, I've been following this guide: [http://ubuntuforums.org/showthread.php?t=145068](http://ubuntuforums.org/showthread.php?t=145068)
I've been able to follow it successfully until now. 
I'm up to part 2: Configuring Xorg. 

It starts like this and keeps going:

> 2. Configure Xorg
Good news you can rework in 24 depth mode
Edit your Screen section and modify your DefaultDepth
Quote:
DefaultDepth 24

Warning this options are necessary !

first activate dri,dbe, glx and all necessary modules like this :
Quote:
Section "Module"
# Load "GLcore"
Load "bitmap"
Load "ddc"
Load "dbe"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

I Can't make any sense of this. I understood the first part because it was just entering commands into terminal, but I don't know where to go to configure these settings.

Any help is appreciated.
Thanks.

---

### Post by diepruis on 2006-07-26
Go have a look at the file "/etc/xorg.conf". Inside this file there's a section titled "Section "Module"". I'm guessing you should have those lines in that section.

The DefaultDepth option can be found in the "Section "Screen"" part. If you need more help, post "/etc/xorg.conf"

---

### Post by Kobalt on 2006-07-26
What you need to do in this step, is to open a file (xorg.conf) and make its parts look like the examples you are given. Ok so :
To open and edit xorg.conf : 
```
sudo gedit /etc/xorg.conf
```
Then you find the section "DefaultDepth" and make it look like this : 
> DefaultDepth 24
Browse the file and find a section that begins like this : Section "Module".
Modify it so it looks like the example your are given (you can copy/paste the example right into the file). 
Do the same for the following sections and their modifications. 
Uncommenting means you remove the " # " before a value (before " dri " for example).

Another hint : to the next step, to create or modify your /etc/gdm/gdm.conf-custom , type this in command line : 
```
sudo gedit /etc/gdm/gdm.conf-custom
```
Copy and paste thet text you're given in the HowTo into the file that appears, instead of the previous lokking like section at the end of the file. 

Here you go,
Cheers !

---

### Post by Crypty on 2006-07-26
Thanks a lot. I have it working now. My Xorg.config was actually located at /etc/x11/xorg.conf but I found it no problem with a quick search. 

I installed the Quinn aiglx/compiz package, which seems to have a lot of plugins with it. Some of the effects are really cool. I think it's a nice improvement over xgl which I had before. One thing that's annoying though is the multi-desktop cube rotation is slow wheras XGL did it smoothly.

---

