---
title: "Dual monitor help"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by Nicallen63 on 2008-11-05
Hello i am new to Ubuntu and I installed Ubuntu on my Macbook a few days ago and have been having trouble with running dual monitors. Both monitors are up and running but from some reason only half of my actual macbook display works when i have both monitors on. I found instructions on how to do this online and changed them around alittle this is exactly what i did to achieve dual monitors:

sudo gedit /etc/X11/xorg.conf

add this subsection:
SubSection "Display"
Depth 24
Virtual 2560 1824
EndSubSection

my virtual is 2560 1824 because one of my macbook display is 1280x800 and the external is 1280x1024.

then close the file and reboot and type this in console
sudo update-initramfs -u
and then reboot again,connect cable and type in console:

xrandr --output VGA --auto --left-of LVDS

I have attached an image of what my desktop looks like, Any help would be greatly appreciated.

---

### Post by tp42 on 2008-11-05
You might try on Ubuntu 8.10 the possibilites in "Preferences>Monitor Resolution"? There you should see both monitors and there should be the possibility to adapt resolution for your external monitor. Besides that, you colud choose there wether you want to mirror your screens or not.

---

### Post by chris_nava on 2008-11-05
> 1280x800 and the external is 1280x1024
You should add the horizontal values but not the vertical ones (assuming your monitors are side by side and not one over the other.)

Try this...
Virtual 2560 800

It gets a bit odd when the monitors don't have the same resolution.

---

### Post by Nicallen63 on 2008-11-05
Thanks for the quick responses heres where i am. I updated to 8.10 and changed the xorg.conf file to 2560 800 and still have the same issue. On a different note after upgrading to 8.10 i can no longer connect to my bluetooth keyboard. I used to connect to it by putting in:

sudo hidd --connect 00:0A:95:39:69:0C

now after i put that in it says sudo: hidd: command not found

Weird stuff

---

### Post by cyberdork33 on 2008-11-05
> **Nicallen63 said:**
> sudo hidd --connect 00:0A:95:39:69:0C

now after i put that in it says sudo: hidd: command not found

Weird stuff
install the bluez-compat package to get hidd back, but you should use the bluetooth applet next to the clock to add your bluetooth devices.

---

### Post by Nicallen63 on 2008-11-05
Alright so new problem, i apparently already have the bluez-compat package already installed. I even went through this tutorial([http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)) and still cant connect to my keyboard. But now this happens when i put in "hcitool scan" i get "Device is not available: No such device" Mind you ive only been using Ubuntu for 3 days now so im still pretty new to all of this.

P.S. still cant get my monitors to play nice with each other. Besides these problems im loving Ubuntu!!

---

### Post by tp42 on 2008-11-06
Today, I tried this  the possibilites in "Preferences>Monitor Resolution" in Ubuntu 8.10 with a beamer, which worked,  too. Tough, perhaps it would be a possibility to remove all custom made entries in xorg.conf, bring it back to the default, restart and try it again with "Monitor resolution"? I work on a Core2Duo Macbook Pro with the out of the box default, open source driver for my graphic card. This ensurers that the "Monitor Resolution" panel works correctly.

---

### Post by Nicallen63 on 2008-11-07
I tried removing all custom entries in xorg.conf and restarted, went into Screen Resolution and still the same affect only now everything is massive as if 800x600 no matter what resolution i set it to. Maybe im just destined to run Ubuntu on one monitor. But on a brighter note my bluetooth keyboard suddenly starting working without me doing anything.

---

### Post by PartisanEntity on 2008-11-08
I have a clean install of Ubuntu 8.10 on my macbook, and when I attempt to apply any changed made in Preferences > Screen Resolution it just freezes when I hit apply to add the virtual resolution (not a system freeze, just the screen resolution app).

Has anyone else experienced this?

---

### Post by Nicallen63 on 2008-11-08
Alright another update for those following my monitor adventures. It seems that Compiz is at fault for most of my problems(i know that macbook video cards are backlisted for compiz but i still wanted to play with it). When Compiz is disabled my dual monitors work.....kinda. I can extend my desktop onto the second monitor but i cant change the resolution on it, it just stays huge and when i do change the resolution anything on the second monitor seems to just overlay on top of the main monitor(if that makes sense to anyone). One step closer to perfection.......

---

### Post by cyberdork33 on 2008-11-08
> **PartisanEntity said:**
> I have a clean install of Ubuntu 8.10 on my macbook, and when I attempt to apply any changed made in Preferences > Screen Resolution it just freezes when I hit apply to add the virtual resolution (not a system freeze, just the screen resolution app).

Has anyone else experienced this?
I have never had any luck with that thing working correctly.

---

### Post by untmdsprt on 2010-04-18
> **Nicallen63 said:**
> When Compiz is disabled my dual monitors work.....kinda. I can extend my desktop onto the second monitor but i cant change the resolution on it, it just stays huge and when i do change the resolution anything on the second monitor seems to just overlay on top of the main monitor(if that makes sense to anyone). One step closer to perfection.......


Thanks, that actually solved my problem of why I couldn't use my external problem.

Now to get my trackpad fixed and I'll be all set. :)

---

### Post by acompay on 2010-04-18
Hello There!
I have a MSI FX5200 video card with s video output. When I connect the TV to the PC via Windows XP Pro a windows pops up that allows me to clone the monitor into the TV and I watch on it what ever is on the monitor. I want to do it with Ubuntu 9.10, how can I do it? Videos in the Internet run much better on Ubuntu 9.10 than on Windows XP Pro. Please, help me!
Regards,

---

### Post by rifak on 2010-04-19
you might want to try this little algorithm that works for me...flawlessly. it has worked for both 9.10 and 10.04 with no problems and i can get full resolution. compiz will work if no extended desktop is used, but compiz should be turned off if you want extended desktop.

first run:
```
gtf 1440 900 60
```

the 1400 900 60 is your desired resolution and refresh rate.

next, copy and past the output of previous command into the xrandr command, for example with previous commands output:

```
xrandr --newmode "1440x900_75.00" 136.49 1440 1536 1688 1936 900 901 904 940 -HSync +Vsync
```

when you run the gtf command, you'll be able to match up what to put into the xrandr command with your specific needs.

next,

```
xrandr --addmode VGA1 1440x900_75.00
```

the VGA1 will need to be changed if you are using DVI or something else, also, the 1440x900_75.00 is the name you gave in quotations from the xrandr command. after you do this, open up the monitor preferences and see if you resolution if available for choosing. if not, do:

```
xrandr --output VGA1 --mode 1440x900_75.00
```

again, changing the necessary information for what youve done. now you can check to see if the desired resolution is available. 

if this work, great, if not, then im sorry lol also, if i am mistaken with what you are trying to do, sorry for wasting your time. i just know that this has worked very well for me in the past and continues to do wonders. finally, i created a .xprofile file in ~/ with these commands (not the gtf one though) and the resolution is detected and outputted automatically. any questions feel free to ask.

---

### Post by snowenvy on 2010-04-22
I love dual monitors.  I can't stand working without a dual monitor actually. 

I used to fight with dual monitors.  Here's a link I use. 

Also, the easiest thing I believe to do is to install the nvidia control panel.  In there you can actually set up dual monitors in a GUI.  And it works great!  

[http://udohomeimprovements.com]("http://udohomeimprovements.com")
[http://northpointmotorsports.com]("http://northpointmotorsports.com")
[http://northpointexteriors.com]("http://northpointexteriors.com")

---

