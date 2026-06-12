---
title: "Having trouble enabling cube effect with Compiz"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-10-27
How can I activate cube effect.  I installed CompizConfig Setting Manager and I checked the cube box and the rotate cube box but I cant figure out how to rotate.  Also, once I installed CompizConfig Setting Manager i lost the hover effect when I hold the mouse over an open window it automatically comes to the top.  I would like to re-enable that effect but i cant figure out how.

thx in advance,

VC

---

### Post by Gone fishing on 2007-10-27
You also need to enable rotate cube in the compiz settings manager it is under Desktop effects

---

### Post by videocheez on 2007-10-27
I have rotate cube enabled  but i need to know what buttons to press to make cube rotate. Upon further investigation, I cliked on the rotate cube button and under the advanced tab the initiate cube button is disabled and i don't know how to enable it.  Any help will be appreciated.

Thx in advance,

VC

---

### Post by por100pre1 on 2007-10-27
Hold **Ctrl + Alt + Left Mouse Button**. Click the **Button** space right next to Initiate and insert this: <Control><Alt>Button1

---

### Post by captain_conrad on 2008-04-12
help!
im also having trouble enabling my cube. I have an ATI radeon 2400 XT inside my Acer extensa 7620 laptop, dual core 1.66, 2gbram. Pc should be able to handle the effects? or do ATI cards give problems? I have compiz efects manager thingie and I have selected the desktop cube and rotate cube plugins, but when I right click on my desktop, change desktop background, and go to the effects tab, it will not allow me to select anything other than "NO EFFECTS". I also saw in a post how do disable my pc seeing my graphics card as blacklisted by putting a # in front of a few lines. My friend set up my ubuntu for me and he said he did that and the cube worked, but somehow now the cube and all other desktop effects don't work. I'd also like to use wobbly windows and stretchy windows but enabling the cube and getting these effects working is main priority right now
please any advice on this will be appreciated
thank you in advance
captain_conrad
absolute totally new to ubuntu linux

---

### Post by captain_conrad on 2008-04-18
um, please help, anybody?

---

### Post by CJ56 on 2008-04-18
Have you tried this -

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

It's the best tutorial I know for getting compiz & the main effects up & running...

---

### Post by captain_conrad on 2008-04-18
that thing is hellova confusing and hellova long.

my problem is that when i left click on the desktop, and click on the visual effects tab, it will not select anything else other than "NONE"

please help, i have no clue where top even begin fixing this

---

### Post by seepage87 on 2008-04-18
It may be confusing and long, but reading is how you learn.  Anyway, do you have the ATI proprietary drivers enabled (fglrx)?  You can enable them via the restricted driver manager.

---

### Post by captain_conrad on 2008-04-18
i totally agree. what are those fgxl driver thingies and how do i do it?
I have the laptop in front of me ( on internet on desktop)

---

### Post by captain_conrad on 2008-04-18
i totally agree about learning by reading. 
anyways
im in my restricted drivers manager

I have an ATI radeon HD 2400 XT

but this thing is only showing  this:

Intel (R) PRO/Wireless 3945 Network Connection driver for Linux

it is enabled and in use

---

### Post by seepage87 on 2008-04-18
Gotcha.  You probably know this, but drivers are what tell your operating system how to use it's hardware.  Right now your computer doesn't know how to use the video card and all it's 3D capabilities.  The thing listed already is your wireless card, which is fine.  Not sure why the ATI driver isn't there.  You should probably get the latest one off the ATI website.  Go here:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

and let us know how you do installing it.  You may also need to install xserver-xgl which you can get through the package manager.

---

### Post by forrestcupp on 2008-04-18
If I were you, I would use [Envy](http://www.albertomilone.com/nvidia_scripts1.html) to automatically install the ATI drivers for you.  It will download and install the latest drivers.  With these drivers, you will be able to run Compiz without using Xgl.

Do that, then try enabling your visual effects, and if it still doesn't work, post back and tell us.

---

