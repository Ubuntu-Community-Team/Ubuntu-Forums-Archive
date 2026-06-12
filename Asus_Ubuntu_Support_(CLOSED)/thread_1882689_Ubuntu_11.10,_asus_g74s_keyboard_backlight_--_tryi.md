---
title: "Ubuntu 11.10, asus g74s keyboard backlight -- trying to turn it on"
date: 2011-11-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ubersoft on 2011-11-17
OK, so apparently the ASUS G74S uses wmi instead of acpi for all its functions like screen dimming, volume control, turning on and off wireless, etc.

In my Kubuntu 11.10 installation, about 80% of those function keys work. The three of note that absolutely do not work are:

F3 - keyboard backlight dim
F4 - keyboard backlight bright
F9 - enable/disable touchpad

This post deals specifically with the keyboard backlight. I haven't been able to find any information about how to get this to work in Linux. The posts for the G73 don't seem to be compatible.

Here's what I know:

The OS appears to have some modules set aside for asus and wmi:

/sys/module/asus_wmi
/sys/module/asus_nb_wmi

In other ASUS-related searches via google, people seem to identify /sys/class/leds as the directory where the keyboard backlight functionality is found (for other models), but all I have in that directory is:

/sys/class/leds/phy0-led

there is a /sys/class/backlight directory, but that's the display backlight, not the keyboard.

There is also a /sys/class/wmi directory, which looks like it has two sub directories that are... well, they look like serial numbers.


... and that's all I know. Now if there was an actual keyboard directory in /sys/class/leds, according to my research I could turn on the keyboard backlight by typing

sudo "echo 1 > /sys/class/leds/keyboard/brightness"

And that would be that. But I don't have such a directory. So I'm stuck.

Can anyone point me in the right direction here?

---

### Post by david_williams on 2011-11-17
I too wish I understood this ... which I don't ... but, by chance I found an odd "trick" that will at least make them turn on ... still not variable, but at least on. 

I was looking for a solution to getting suspend/resume to work (for me, on my G74SX, at least, the sleep fn key would work, but wouldn't actually resume correctly). 

There's several "solutions" out there, but I think the easiest to follow are the instructions at 
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug) 

But, in case it matters, I initially implemented the instructions at 
[http://ubuntuforums.org/showpost.php?p=9180298&postcount=7](http://ubuntuforums.org/showpost.php?p=9180298&postcount=7)
(including using chmod +x as mentioned in 
[http://ubuntuforums.org/showpost.php?p=9180693&postcount=8](http://ubuntuforums.org/showpost.php?p=9180693&postcount=8)

So, at any rate, now after I "resume" the keys backlight LEDs come on!

As far as I know, its just some fluke of some bios related function, or something .... but ... at least they are on. The fn keys still don't control them. 

I thought I'd pass along this "finding" in case it leads to at least some practical value until the "real" fix comes along. 

FYI, a couple of other "fixes" mentioned in 
[http://ubuntuforums.org/showthread.php?t=1768551&page=7](http://ubuntuforums.org/showthread.php?t=1768551&page=7)
led to a few other things being more functional for me on my G74SX; improved screen brightness control from fn keys, and got my SDCardReader working. (For volume control, my FN keys worked out of the box for Ubuntu 11.10 but not earlier versions).

---

### Post by ubersoft on 2011-11-19
Well that's weird... but it works for me too.

---

### Post by david_williams on 2011-12-05
No (easy) solution, but to continue to "report from the trenches", I compiled my first "kernel" over the weekend (3.1.4) and used it, instead of what comes from Ubuntu's distribution repository (3.0.0-13) and the keyboard backlight and F3/F4 finally work "out of the box"! 

There does now, exist, a file similar to what the first comment in this thread was looking for: 
/sys/devices/platform/asus-nb-wmi/leds/asus::kbd_backlight/brightness
that I don't recall being there before ... but, I doubt, just having the file there would fix anything (and, oddly, it seems to always have a value of "0", no matter what brightness I set with the keys). 

Compiling the kernel and getting other things to work with it (like the proprietary display drivers! :) wasn't "easy", but not too hard either. I wouldn't recommend it for a "production" machine ... could easily effect other parts of Ubuntu that I just don't happen to use. Mostly reporting that "there is hope for the future" :)

---

### Post by CylnZ on 2012-01-06
Hi, I was searching around to find any new hacks for linux and the g74sx and found your thread here.  I found a thread for the g53 and have adapted it to work on our g74sx  no, my keys dont work either but you can write up a script to run at startup, something like this:  Now, (LOOK) the path here is for Fedora 16 xfce!  ```
echo 1 > /sys/devices/platform/asus-nb-wmi/leds/asus\:\:kbd_backlight/brightness
```  this works for me every time if you run it as ```
su -
```  You might try using your path with the rest of this syntax. That's what I did when I found it for the g53 under arch.  Hope this helps.

---

