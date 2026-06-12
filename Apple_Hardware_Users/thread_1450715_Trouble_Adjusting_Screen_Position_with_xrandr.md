---
title: "Trouble Adjusting Screen Position with xrandr"
date: 2010-04-09
forum: Apple Hardware Users
---

### Post by Relative Prime on 2010-04-09
Hi there,

I am running a dual boot conifg with OSX and Ubuntu PPC (karmic) on a 2004 G5 and everything is working pretty well - very well actually. The last thing I am trying to adjust is such a simple thing, but I just can't seem to get it. 

In Ubuntu, the screen position is shifted to the right, covering the scroll bar of windows and the trash can.

No problem, just use xvidtune, adjust the screen as I want and create a custom modeline right? Well, it does not seem to work.

Here is what I did:

Using xrandr I created a --newmode and then used --addmode to add it to the output I am using (default):

```
mieren@G5-Ubuntu:~$ xrandr --output default --newmode 1680x1050_new 146.25   1680 1820 1996 2268   1050 1053 1059 1089 -hsync +vsync

mieren@G5-Ubuntu:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm

<other resolutions omitted>
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
   320x240        75.0     73.0     60.0
  1680x1050_new (0x16a)  146.2MHz
        h: width  1680 start 1820 end 1996 total 2268 skew    0 clock   64.5KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   59.2Hz
```So far it looks good. Then I add the mode to the output:

```
mieren@G5-Ubuntu:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050

   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
   320x240        75.0     73.0     60.0  
   1680x1050_new   59.2 

```Notice how the new mode now lacks the rest of the config information specified in the --newmode above, not sure if this is normal.

I can change to the new mode, and the resolution is correct, but the screen is still not adjusted. There is no difference switching between the 1680x1050 and the 1680x1050_new modes - the screen may flash, but the position does not change. 

(I also tried adding a mode line to /etc/X11/xorg.conf screen section, but it also has no effect. Actually, there was no xorg.conf existing at all, so I created a minimal one.)

Any ideas? It is really annoying to have to adjust the screen position using the monitor controls on every reboot, so I would greatly appreciate any help on this. 

Thanks,
Relative Prime

---

### Post by linuxopjemac on 2010-04-09
maybe this one?:
[http://mac.linux.be/content/g5-imac-widescreen-shift-right](http://mac.linux.be/content/g5-imac-widescreen-shift-right)

---

