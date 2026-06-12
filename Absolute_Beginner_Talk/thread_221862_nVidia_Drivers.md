---
title: "nVidia Drivers"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Josh_b on 2006-07-24
Hi,

I'm running dual 7900GT's. Should I install the package (through synaptic, nVidia-glx) or get the official drivers from the nVidia website?:???: 

Thanks in advance,
Josh

---

### Post by Kobalt on 2006-07-24
nvidia-glx through synaptic should be the latest avaliable. To install it you'd better install this package first : 
```
$ sudo apt-get install linux-restricted-modules-`uname -r`
```
And make a backup of your Xorg.conf file, just in case...
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```
Then you can install your driver and a tool to configure and tweak your graphic card :
```
$ sudo apt-get install nvidia-glx

$ sudo nvidia-glx-config enable
```

---

### Post by frodon on 2006-07-24
This guide will tell you all you need to know :
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by richbarna on 2006-07-24
In my sig too.
|
|
v

---

### Post by Josh_b on 2006-07-24
Yep that worked fine.:-D  Although, does it support SLi?

---

### Post by mcvos on 2006-07-24
I'll check frodon's link. I followed the instructions in [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#nvidia]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#nvidia"), and they are wrong. Firstly, it says my GeForce4 mx440 requires nvidia-glx, when in fact it requires nvidia-glx-legacy. Took a while before I figured that one out.

But after getting the proper drivers and reconfiguring the xorg.conf, the resolution is still stuck at 640x480.

---

### Post by frodon on 2006-07-24
mcvos, often this resolution problem is not due to the drivers but to the xorg.conf file configuration.
Did you add the horizontal and vertical refresh rate parameters of your screen in your xorg.conf file ?

---

### Post by mcvos on 2006-07-24
No. I used 'dpkg-reconfigure xserver-xorg' to configure the xorg.conf, and it said that if I didn't know the refresh rate, a decent one would be guessed or asked from the monitor itself (a 21" Compaq 1220, in case that helps).

I haven't checked if that tool actually added refresh rates to the xorg.conf. I'll do that tonight.

---

### Post by mcvos on 2006-07-25
Turns out my GeForce4 MX 440 is an extra weird video card. [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") has a special (and pretty long) section just for my videocard (and two others that are no doubt equally weird).

Tonight I'll use those instructions to fix it. Would it be possible for the next Ubuntu release to automatically detect these weird cards and treat them properly?

---

### Post by Jeff Johnston on 2006-07-25
I just got a new monitor. It is a Hanns-G JW199D. Very cool widescreen monitor. The problem is I would like to run at a lower refresh rate. Currently I am at 1440X900@75 and would like to run at 1440X900@60. I have looked at the specs for my monitor and it does not list what the horizontal or verticle refresh rates should be. The only mention I could find was it said to look at what my video card supports...whatever that mean :(. 

My video card is an Nvidia 6100. 

Is there something safe I can set my horizontal and verticle to to get a 60 refresh rate?

---

### Post by Jeff Johnston on 2006-07-26
I just did the ddcprobe command and it says my horizontal and verticle are:

	HorizSync       30-83
        VertRefresh     50-76

So I updated my xorg.conf file but I still do not get an option to select a 60 refresh rate in the Screen Resolution GUI in System Preferences.

Also, am I crazy for wanting a 60 refresh rate? I thought with and LCD that 60 was more preferred. I have only used CRT's before and there the higher the better of course.

---

### Post by Jeff Johnston on 2006-07-26
Ok, I got it. I forced the refresh rate by taking out all the other ones and explicitly saying 60. This seems like a nice refresh rate.

Modes		"1440x900@60"

---

### Post by Josh_b on 2006-08-09
So do the drivers/linux support SLi?

---

### Post by tseliot on 2006-08-11
> **Josh_b said:**
> So do the drivers/linux support SLi?

yep.

You must enable it though.

You can do it in this way:
```
sudo nvidia-xconfig --sli=Auto
```

---

### Post by Josh_b on 2006-08-18
I typed that in and received the following messagee:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

And then the prompt line thingy came backup. Is that what its supposed to do, or didn't it work?

---

