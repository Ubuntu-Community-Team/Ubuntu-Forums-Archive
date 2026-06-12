---
title: "Screen resolution"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Curulin on 2006-11-05
I want to change to a higher resolution, but under System -> Preferences -> Screen Resolution I can only choose between 640x480 and 800x600. 
How do I get more options?
I have a 17" monitor.

---

### Post by spud42 on 2006-11-05
try this in a terminal window
sudo dpkg-reconfigure xserver-xorg

im having similar problems with a dell d620 laptop getting the higest resolution of 1280 800 . this is what ive been told to try. give it a go .

---

### Post by Curulin on 2006-11-05
Since I have a desktop computer, I'll rather wait for more answers.

---

### Post by bulldog on 2006-11-05
Or install your graphics drivers if you haven't done so.

---

### Post by spud42 on 2006-11-05
doesnt matter if its a desktop or not , xserver is your interface to the world

---

### Post by bulldog on 2006-11-05
> **spud42 said:**
> doesnt matter if its a desktop or not , xserver is your interface to the world

Oeps,didn't realize it's **that** important..............:D

---

### Post by spud42 on 2006-11-05
well maybe i exagerated a little  lol

---

### Post by bulldog on 2006-11-05
Oke,but did you install some graphics driver?

If not you can only use the standard config [read safe-mode] for your graphics.
Installing the driver will enhance the capabillity's of your card.

And if that doesn't compute for some reason,you can use the reconfigure option.

Reconfigure a basic install won't change much I suppose.:D

---

### Post by Curulin on 2006-11-05
Which leads me to the next question:
How do I install these drivers?
And do I have to install them at all? Weren't they installed while I installed Ubuntu?

---

### Post by svan2004 on 2006-11-05
I have had the same problem. You will have to edit xorg.conf:

open terminal

sudo gedit /etc/X11/xorg.conf

Find Section "Screen" and add the resolutions you are missing.
Like this: 

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Save and log out/in.

---

### Post by bulldog on 2006-11-05
> **Curulin said:**
> Which leads me to the next question:
How do I install these drivers?
And do I have to install them at all? Weren't they installed while I installed Ubuntu?

How did things go in windows again??Didn't you have to install your drivers??

They are not installed by default,even Ubuntu is not that advanced.:D 

That said,it's important to know what kind of graphics you have to install drivers,you can't use ATI drivers for a nVidia card I think.

If you're a little insecure about installing drivers,take a look at automatix2,this amazing app can install a whole lot more for you,like codecs,P2P programs,java,swiftfox,opera and so on.
And with a little luck if your graphics isn't that exotic,your drivers for the card.
Take a look for yourself,

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by BWF89 on 2006-11-05
> **spud42 said:**
> try this in a terminal window
sudo dpkg-reconfigure xserver-xorg
Thanks for the fix, I was having the same problem this morning when I booted up and found that for whatever reason Ubuntu changed my resolution. I wrote down that command down on my notepad in case I need it later.

---

