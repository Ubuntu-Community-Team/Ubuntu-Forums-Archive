---
title: "[SOLVED] Graphics problems"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by steve0961 on 2008-03-29
I have an ATI Radeon Mobility X1400 graphics card in the laptop I have Ubuntu installed on. I downloaded the fix for the drivers through the Restricted Drivers window. I was having problems with it allowing me to choose my native resolution on 1280x800 and the driver fix fixed that, but I still cant enable visual effects. Whenever I try to turn on normal or extra visual effects in the appearance preferences menu, an error pops up saying "The composite extension is not available" How would I fix this? Thanks.

---

### Post by benste on 2008-03-29
Did you install XGL things?

---

### Post by steve0961 on 2008-03-29
> **benste said:**
> Did you install XGL things?

Im not sure. I don't think I did, considering I spent all last night tackling my problems with my wireless card and didnt do too much after that besides go to bed. If it wasnt installed in the base install, then probably not. Where would I find them and how do I install them?

---

### Post by benste on 2008-03-29
I'm sorry it's named > fglrx it seems to be the closed source driver of AMD
maybe you could first try
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by steve0961 on 2008-03-29
> **benste said:**
> I'm sorry it's named  it seems to be the closed source driver of AMD
maybe you could first try
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

That's what I meant by driver fix, sorry I couldnt remember exactly what they were called. What else could be causing it?

---

### Post by benste on 2008-03-29
Once again, do you use your 3d grafic and only compiz is broken??

try "glxgears"

is there a smoothy output?

---

### Post by steve0961 on 2008-03-29
> **benste said:**
> Once again, do you use your 3d grafic and only compiz is broken??

try "glxgears"

is there a smoothy output?

Sorry but I didn't understand a single part of that. The first sentence doesnt make too much sense to me, i have no idea what glxgears is, and i don't know what you mean by a "smoothy" output. Alls I know is that I'm using the fglrx drivers and whenever I try to turn on visual effects, it says "The composite extension is not available".

*EDIT* I typed glxgears into the console, and the frame with rotating gears popped up, it says in the console "8207 frames in 5.0 seconds = 1641.322 FPS". Does this mean it worked?

---

### Post by benste on 2008-03-29
I don't no this frames, only 3 (circles with corners) which are rotating, whe this action goes fluently, than the3d grafic driver is in use

---

### Post by xeth_delta on 2008-03-29
Let's first find out whether you have 3D hardware acceleration enabled. Open a terminal and type
```
glxinfo | grep -i direct
```
Post the output.

---

### Post by benste on 2008-03-29
god to know that an expert will help him, I only knew the looking way of glxgears.:)

---

### Post by lswest on 2008-03-29
to enable the composite you have to go to the end of your xorg.conf file and add the lines
> Section "Extensions"
Option "Composite" "Enable"
EndSection to enable the composite extension.  From there on it should work.  If the lines are already there, just change the last bit to "Enable".

also, open the xorg file with ```
gksudo gedit /etc/X11/xorg.conf
```

**remember to back up your xorg.conf file** before just in case with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
to restore just do ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

i'm going to assume he has 3d acceleration, as otherwise he would have gotten other errors when trying to start compiz.

---

### Post by forrestcupp on 2008-03-29
If you're using the ATI drivers from the Restricted Drivers Manager, then you need to have Xgl installed, or you can't use Compiz.  Just open a terminal and type
```
sudo apt-get install xserver-xgl
```
To install it, then reboot, and you should be able to use the Visual Effects.

---

### Post by lswest on 2008-03-29
@ the OP, try forrestcupp's suggestion first, and if that still doesn't work, try mine.  The reason for this is that i'm not sure if the fix i named above skips over the xgl system, it's what i use on my PC but i can't remember if i have xgl installed or not (typing this from my laptop atm).

---

### Post by forrestcupp on 2008-03-29
> **lswest said:**
> @ the OP, try forrestcupp's suggestion first, and if that still doesn't work, try mine.  The reason for this is that i'm not sure if the fix i named above skips over the xgl system, it's what i use on my PC but i can't remember if i have xgl installed or not (typing this from my laptop atm).

Well, the newer drivers don't require Xgl, and you need what you said for them.  But the ones that are in the Restricted Drivers Manager are old drivers that still require Xgl.  I think as long as you have the DRI with the RDM drivers, Xgl will just work because it just makes a new desktop with opengl.

---

### Post by lswest on 2008-03-29
Thanks, never knew that, i assumed that xgl was just another package people needed, but seeing as how i use nvidia i never bothered read up on it (because the card in my PC is a RADEON 9600XT and the drivers from ATI/AMD work fine, with adding the composite bit gets everything working just fine).  So thanks, i always enjoy learning something new ^^ (by the way, feel special-->that was the first thanks i've given XD)

---

### Post by steve0961 on 2008-03-29
> **forrestcupp said:**
> If you're using the ATI drivers from the Restricted Drivers Manager, then you need to have Xgl installed, or you can't use Compiz.  Just open a terminal and type
```
sudo apt-get install xserver-xgl
```
To install it, then reboot, and you should be able to use the Visual Effects.

Thank you! That worked perfectly. Im giving thanks to you and lsweet for your help. I'm starting to like Ubuntu more and more :P

---

### Post by lswest on 2008-03-29
Thanks for the thanks ^^ always happy to help :)

---

