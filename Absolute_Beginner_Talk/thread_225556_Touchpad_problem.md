---
title: "Touchpad problem"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by aburd on 2006-07-29
Ok I have ubuntu installed on my HP Pavilion zv5000 AMD64 laptop. I've been messing with it and love it, but I have one problem I can't find a solution for. My touchpad is acting very crazy. It suddenly becomes "clicked" without me doing anything. At these points it either highlights or selects things that I am not trying to select or highlight. Occasionally dragging it across the desktop will create one of those highlight boxes as I move the mouse.

Are there any solutions out there? I saw one that involved editing my drivers or something, but I have no idea how to do that. Any ideas?

And again, I'm sorry about my earlier, much more idiotic post...

---

### Post by aburd on 2006-07-29
[http://www.ubuntuforums.org/showthread.php?t=45142&page=2]("http://www.ubuntuforums.org/showthread.php?t=45142&page=2")

This first post seems like it could help, but I just don't know how to use this stuff. I have downloaded this "synaptics touchpad driver" from the first link in the post, but I don't know how to install it.

---

### Post by aburd on 2006-07-30
So I just ran across [this.]("http://gentoo-wiki.com/HARDWARE_HP_Pavilion_zv5000#Touchpad")

It says this:

> To use the touchpad in a console requires no extra drivers. Edit the /etc/conf.d/gpm file. The configuration should look something like this:

MOUSE=ps2
MOUSEDEV=/dev/input/mice

I can switch to the console version. So how can I get to the /etc/conf.d/gpm stuff? Any help would be very appreciated.

---

### Post by aburd on 2006-07-30
So I installed a second driver in the place of the xorg driver, and now the mouse moves like really short distances. It completely sucks. 

All I want is to get the xorg driver back and disable the tap to click "feature", which seems a bit too sensitive in this case.

Again, any help at all would be appreciated.

This:

> Install the xfree86-driver-synaptics package in Synaptic or your favorite package manager. The command would be
Code:

sudo apt-get install xfree86-driver-synaptics

This will automatically uninstall xserver-xorg-input-synaptics.

Next, create a sym-link to the driver in your xorg drivers directory
Code:

sudo ln -sf /usr/X11R6/lib/modules/input/synaptics_drv.o /usr/lib/xorg/modules/input/synaptics_drv.o


Reboot your computer

is what I did. Please if you know how to reverse this or just modify it so that I can move my mouse more than an inch and disabling the "tap to click", I would be forever in your debt. Thanks.

---

### Post by aburd on 2006-08-04
I actually found an answer! I repeated my question along with a link to this thread over on AskMetafilter:

[http://ask.metafilter.com/mefi/43623]("http://ask.metafilter.com/mefi/43623")

And found the answer. Basically I just retrieved my old driver (the xorg driver), made a backup copy, and edited it using gedit. I had no idea that you could just edit the files by doing something like:


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
sudo gedit /etc/X11/xorg.conf

The first line makes a backup. It will look like nothing happened by in fact very important things went on. Then the "sudo gedit" section will pull up a text file with the code of the driver (along with an explanation of what the driver is doing). It is simply just a matter of adding lines in the appropriate format to the driver.

So I just added the following lines to the "input device" "synaptics touchpad" section of the driver info:

Option "MaxTapTime" "0"
Option "MaxTapMove" "0"
Option "MaxDoubleTapTime" "0"

If anyone else ever has any issues with attempting to do this please email me at andrew dot burd at gmail dot com.

Thanks!

---

### Post by The Shadow on 2006-08-04
Thanks for the post; I have been having the same problem as your first post. I found some "solutions" but none of them were permanent. It would always revert back to the same problem. I will try this when I get home tonight.

---

