---
title: "XServer Issues /dev/wacom?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by pingbat on 2006-08-21
Okay,

X-server will not boot.

The last couple of lines in the log file consist of the following repeated many times:


```
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
```


At the very end of the log is this line

```
(II) Configured Mouse: ps2EnabledDataReporting: succeeded
```



Ummm... Help :-k

---

### Post by amohanty on 2006-08-21
This is something wierd with teh Dapper installer. I ran into this too, so heres what you need to do:

1. Get to the recovery console and in the terminal type:
> sudo dpkg-reconfigure xserver-xorg
Then just click through the windows.

2. Edit /etc/X11/xorg.conf using
> visudo /etc/X11/xorg.conf
Now in that, find all Section...EndSection parts that refer to wacom.
**Do not press the character 'a' at any time, vi goes into edit mode and you dont want that**
then infront of each line (incl. the Section and EndSection lines) type **dd**. This will delete the line for you. Once you are done type **ESC-w-q** (without the '-' chars). This will save the file and quit the editor.

Reboot and see if it works.

HTH
AM

---

### Post by pingbat on 2006-08-21
Thanks but no joy,

Xserver still won't start.

It says that it failed to initialise the glx driver

I'm removing the glx option from the X11 config file and trying again.

---

### Post by pingbat on 2006-08-21
That didn't work either, I'm looking at the log file and can't see any obvious errors...

I was trying to enable xgl before the reboot. Could it be something to do with that?

I am going to reinstall the nvidia drivers and try again.

---

### Post by amohanty on 2006-08-21
Ok try to uncheck everything in the options pane and start x.
In theory it should work because X does not need all module to fire up. 

HTH
AM

PS: could you post the contents of /var/log/X11.log 
warning: its damn long

---

### Post by pingbat on 2006-08-21
okay,

xserver failed to start again.

I successfully enabled GLX then, on reboot, got a Blue flickering screen with lots of noise on it. 

I'm assuming that that is not good.

I restarted with the button on my case and then got the original wacom error again...

---

### Post by pingbat on 2006-08-21
> **amohanty said:**
> 
PS: could you post the contents of /var/log/X11.log 
warning: its damn long

Umm, no such file... Do you mean /var/log/Xorg.93.log

Disabling all the options and trying again . . .

Thanks for the help amohanty.

---

### Post by amohanty on 2006-08-21
Yes. Sorry about the mistake, had forgotten what the logfile was called. 

Also by default X starts on disply 0 so you ought to have a file called **Xorg.0.log**. If you dont that's another problem you might have.

Any post the contents of the file if you can.

AM

---

### Post by frup on 2006-08-22
im having the same issue... i just installed XGL/compiz the ubuntuguide way and its not working... /dev/wacom is not found (i had a look and its not there too)

im on another computer now... but how would i access the internet to post here from my computer in terminal? i did wget ubuntuguide.org to check every setup stage with no luck i followed everything perfect...

running GDM (prints errors) and then X gives me a black and white dotted screen with mouse movement... cursor X

running the script "thefuture" created in the guide prints compiz:real some error or something...

also whats the ls command to break at end of page? sofar using -r has helped but what if a dir im looking in is even longer and i want to see something in the middle?

---

### Post by George_S on 2006-08-22
I received an Ubuntu update this evening. It was something regarding the X Server. I clicked on the Update button and everything went throught okay. I continued working in Ubuntu for the next couple of hours. However, when I restarted the system I got the "Failed to start the X srver ....." message. I did not install any new software, nor change the settings in any way.

I tried the solutions described in this thread, but to no avail. The question is, why would Ubuntu present me with an update that would mess up the X server??

---

### Post by George_S on 2006-08-22
Ok, after trying everything else, I had to downgrade to version 10.0 by doing this:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
startx

However, now that I am back in Ubuntu, I keep getting the update notification  again:

xserver-xorg-core
New version: 1:1.0.2-0ubuntu10.3 (Size: 3532k)

Any way to stop this update from popping up given the fact that it's buggy?

---

### Post by frup on 2006-08-22
OK that worked for me... even though i dont think i updated/got the update :S

Interestingly i have lost all my firefox book marks etc.. is this standard? 

note in the last hour i have:

attempted to install XGL and Compiz (following guide at ubuntuguide.org)
reconfigured the xserver (which didnt seem to be the problem)
Modified and reverted dm.conf-custom
downgraded Xserver-xorg-core

my gfx card is Geforce 4 ti 128mb 4200 (i think thats the number?) is this not capable of xgl/compiz?

---

### Post by pingbat on 2006-08-22
Okay,

similarly to frup, I have attempted xgl compiz and everything froze up.

I think i remember installing the xserver update and suspect that it is that causing the issues we are seeing here.

I think this might be worthy of a new thread but hey, I'm a total noob when it comes to linux.

Oh yeah, everything is acting all wierd with this xserver version. I'm going to reconfigure it to see if it helps.

---

### Post by amohanty on 2006-08-22
Apparently last night's (PST) xorg xserver update was botched because I could not fire up X today morning. Howver an **apt-get upgrade** showed yet another xorg xserver update, on application of which, everything was working again. Try that and see if it fixes your problem.

HTH
AM

---

### Post by amohanty on 2006-08-22
..

---

### Post by monkeeshyne on 2006-08-25
I have been having a similar problem.  Well, it's not really a problem--more of a nuisance.  I have several entries in my xorg.conf referring to /dev/wacom.  Curiously, I don't have a wacom tablet, but if I comment those lines out, X fails to start.  I was thinking that maybe it was trying to use the wacom driver for my touchpad (I'm on a Latitude D620, and my the margins of my touchpad can be used to automagically scroll).  But that feature shouldn't be required to start X, should it?

Like I said, this is only a nuisance, as (K)ubuntu works flawlessly on my system.

---

