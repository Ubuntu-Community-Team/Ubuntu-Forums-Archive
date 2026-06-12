---
title: "Can't move any window.. workspace gone."
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by diablofatt on 2007-09-28
Hi I am kinda new..

I installed the desktop effects that comes with ubunutu.. it seems like after that I can no longer move ANY window. I noticed this when I opened giam and I tried to move it to the right side of my screen. The close and minimize buttons are gone on everything.. that is my main problem i am concerned with. 

Also if I go to another workspace there is NOTHING there. By nothing I mean I have to tap my power button on my tower and click on the log out option to manage ubuntu. 

Thank you for reading.. but id like to be able to move my windows more then anything.
:cool: 

:twisted:

---

### Post by overdrank on 2007-09-28
> **diablofatt said:**
> Hi I am kinda new..

I installed the desktop effects that comes with ubunutu.. it seems like after that I can no longer move ANY window. I noticed this when I opened giam and I tried to move it to the right side of my screen. The close and minimize buttons are gone on everything.. that is my main problem i am concerned with. 

Also if I go to another workspace there is NOTHING there. By nothing I mean I have to tap my power button on my tower and click on the log out option to manage ubuntu. 

Thank you for reading.. but id like to be able to move my windows more then anything.
:cool: 

:twisted:

Hi, did you enable your restricted drivers and what model video card are we talking about?

---

### Post by diablofatt on 2007-09-30
I believe I did enable them after they were installed. I received a pop up and the box was checked. 

I have a geforce 6800..

they come back if i disable the effects.. but i do like them. also i cant see my terminal or download windows with the effect enabled

---

### Post by overdrank on 2007-09-30
> **diablofatt said:**
> I believe I did enable them after they were installed. I received a pop up and the box was checked. 

I have a geforce 6800..

they come back if i disable the effects.. but i do like them. also i cant see my terminal or download windows with the effect enabled

Ok can you post the output of this command in the terminal 
```
cat /etc/X11/xorg.conf

```

---

### Post by izhar81 on 2007-11-25
Currently have same problem too... cannot type anything in terminal.. just have white square, dont have any minimize, maximixe and x button... canot gramb windows by holding a click..

i'm using FX5500

but i f i disabel all effect, the terminal come back to normal.....

---

### Post by izhar81 on 2007-11-25
Currently have same problem too... cannot type anything in terminal.. just have white square, dont have any minimize, maximixe and x button... canot gramb windows by holding a click..

i'm using FX5500

but i f i disabel all effect, the terminal come back to normal.....


please help...

[img]http://img254.imageshack.us/img254/751/screenshotdx1.png[/img]

---

### Post by overdrank on 2007-11-25
> **izhar81 said:**
> Currently have same problem too... cannot type anything in terminal.. just have white square, dont have any minimize, maximixe and x button... canot gramb windows by holding a click..

i'm using FX5500

but i f i disable all effect, the terminal come back to normal.....

Then you may want t add this to you xorg
  Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
In the device section using the command ```
gksudo gedit /etc/X11/org.conf
```but back up you xorg first
To copy Xorg
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
To restore backup
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by izhar81 on 2007-11-25
> **overdrank said:**
> Then you may want t add this to you xorg
  Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
In the device section using the command ```
gksudo gedit /etc/X11/org.conf
```but back up you xorg first
To copy Xorg
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
To restore backup
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

thank you overdrank buddy. :)

I dont know either a restart or because your tips, but now the problem solved.. I just followed your guide and it is ok now. Tq very much for your help.
May i buy you some drink? :popcorn:

---

