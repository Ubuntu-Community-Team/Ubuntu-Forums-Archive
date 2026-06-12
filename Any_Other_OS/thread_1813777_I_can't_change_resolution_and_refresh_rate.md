---
title: "I can't change resolution and refresh rate"
date: 2011-07-28
forum: Any Other OS
---

### Post by yoahim on 2011-07-28
Hi
I am new in Linux and I can't change  resolution and refresh rate. Currently I'm using Mint 11 (on Ubuntu I had same problem) At beginning i was stuck in 1280x1024, but after editing xorg.conf system was forced to set 1024x768. This is my present file:> Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
    VendorName "CPQ"
    ModelName "COMPAQ S710"
    HorizSync 30.0 - 70.0
    VertRefresh 50.0 - 160.0
    Modeline "1024x768_85.00" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor "Configured Monitor"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1024x768" "800x600" "640x480"
    EndSubSection
EndSectionBut 
 Now i've got 1024x768 and 60Hz, despite in  "Monitors" says that is 0Hz - and i can't change it. I'd like to set to 85Hz. "Hardware drivers" doesn't find any drivers. When i set "ati" or "radeon" in xorg.conf screen is going black. 

To be able to install linux i had to use nomodeset and safe graphic mode (-xforcevesa)

------
Mint 11, ATI Radeon 9800Pro and monitor Compaq S710

---

### Post by thefasterblueone on 2011-07-28
The last post on [this page](http://ubuntuforums.org/showthread.php?t=1221221) might help.

---

### Post by seawolf167 on 2011-07-28
What is the output of 

```
sudo lshw -class display
```

to see if we can find you any available drivers or more info on your graphics card.

---

### Post by realzippy on 2011-07-28
Sorry for jumping in,but 
OP already mentioned:
ATI Radeon 9800Pro
Means,there is no driver.
So,"the last post" from link in post #2 won't help also.
Suggest to start with

```
xrandr -q
```

---

### Post by seawolf167 on 2011-07-28
> **realzippy said:**
> Sorry for jumping in,but 
OP already mentioned:
ATI Radeon 9800Pro
Means,there is no driver.

Oops, totally missed that!

What about reseting xorg?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by realzippy on 2011-07-28
Seems as OP edited xorg.conf to make 1024x768_85.00 run,so
resetting it won't help...:

Modeline "1024x768_85.00" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync

I think it already runs 1024x768 at 85.00 (Monitors GUI simply is lying,
0 Hz is impossible ;_)  ).
xrandr -q should show current status.

---

### Post by seawolf167 on 2011-07-28
Thanks for the explanation realzippy!

---

### Post by yoahim on 2011-07-28
> **thefasterblueone said:**
> The last post on [this page]("http://ubuntuforums.org/showthread.php?t=1221221") might help.
I installed by this way, but i can't activate this drivers. When I click on "activate" , i get "Downloading and installing driver" window and after few seconds it disappears.

> **seawolf167 said:**
> What is the output of 
```
sudo lshw -class display
```to see if we can find you any available drivers or more info on your graphics card.

```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Radeon R350 [Radeon 9800 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d8000000-dfffffff ioport:c000(size=256) memory:e9000000-e900ffff memory:e8000000-e801ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R350 [Radeon 9800 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
       resources: memory:e0000000-e7ffffff memory:e9010000-e901ffff
```**xrandr -q**
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600         0.0  
   640x480         0.0 
```
I know it's impossible to have 0Hz, but i can check refresh rate in monitor's OSD and it's 60Hz.

---

### Post by realzippy on 2011-07-28
Honestly I **do not know** if the VESA driver *can* get about 60 Hz Vrefresh...quick googling finds no answer,only other people having the problem to increase refresh rate with vesa ....

Have you ever tried to run the 
Modeline "1024x768_85.00"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync

with xrandr?

---

### Post by Perfect Storm on 2011-07-28
Moved to Other OS/Distro Talk.

---

### Post by yoahim on 2011-07-29
> **realzippy said:**
> Honestly I **do not know** if the VESA driver *can* get about 60 Hz Vrefresh...quick googling finds no answer,only other people having the problem to increase refresh rate with vesa ....

Have you ever tried to run the 
Modeline "1024x768_85.00"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync

with xrandr?

It doesn't work.

---

### Post by realzippy on 2011-07-29
...can you post the xrandr commands (newmode,addmode aso) (and its outputs)
you did run?

---

### Post by yoahim on 2011-07-29
```
$ xrandr --newmode "1024x768_85.00" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync
xrandr: Failed to get size of gamma for output default
```

```
xrandr --addmode VGA1 1024x768_85.00
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "VGA1"
```

I don't know what to put instead "VGA1", i tried several names such as vga-0,vga0,vga-1,screen 0,dvi1 etc. None of them works.

---

### Post by realzippy on 2011-07-29
It is "default" , nothing else...:

```
xrandr --addmode default "1024x768_85.00"

```
and
```
xrandr --output default --mode "1024x768_85.00"
```

---

### Post by yoahim on 2011-07-29
It doesn't work either.
```
xrandr --addmode default "1024x768_85.00"
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1024x768_85.00"
```

---

### Post by realzippy on 2011-07-29
*xrandr: cannot find mode "1024x768_85.00"*

???

thought you have run

xrandr --newmode "1024x768_85.00" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync


before?
Can you show again the output from

```
xrandr -q
```


...or have you logged out/rebooted meanwhile?

---

### Post by yoahim on 2011-07-29
You are right, i did reboot. Now I can set to 85Hz in monitor's GUI, but after applying, it doesn't give any effects.

---

### Post by realzippy on 2011-07-29
So you increased from 60 Hz to 85 Hz..
that's all I can do for you.
Normally you should notice the increased refresh rate..

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

