---
title: "Macbook (core2duo 13&quot;) + Gutsy Tribe-5"
date: 2007-09-06
forum: Apple Intel Users
---

### Post by ideasman42 on 2007-09-06
Hi, I recently bought a macbook core2duo 1gig ram 80g hdd. etc

booted up and installed gutsy CD and didnt even take a peek at OSX ;)

In general Im happy with it (Iv been a gentoo/slackware user for some years) but want a distro for my laptop that I dont need to fiddle with.

This is mostly for me to do programming on and Iv installed eclipse and have a nice development environment...

Iv also installed the menu updates that come daily with gutsy...

ok... Here are a list of the problems Iv had so far.

* Wifi isnt recognized, I dont really care about this since I wont use it but it would be good if it worked. it seems everyones aware of this. - madwifi etc.

* no webcam (iSight) again, I dont really care.

* Touchpad. Would be good if Gutsy installed the touchpad configuration tool by default (on laptops at least) and enabled it in xorg.conf (I installed but it told me I needed to edit my xorg.conf to use it)

* Volume, The mixer see's the base/treble as the master volume. so the volume control in the corner of the screen wont work out of the box (this is a bit annoying - an alsa bug I guess) I switched it to adjust the PCM volume, ok for now.

* When I change the volume in totem. then click on a window behind totem, the volume control slider stays on top. I need to click back to totem and then away from the slider on the totem window to get the slider to go away (probably a totem/gtk bug)

* In the screen settings I tried rotating the screen (not sure why just did...) and it flickered, popuped up a new blank X with a dialog "Do you want to keep this setting?" . I pressed cancel and it rebooted the laptop. - probably the only crash I have had.

* To access the FKeys I need to press the laptops Fn key, otherwise they are multimedia keys by default. I think this isnt todo with ubuntu however its annoying. would be interested to know if there is a way to change this.

* No way to change the screen brightness at all! - one of the bigger problems, the brightness keys on the keyboard do nothing. as far as I can tell there is no way to do this.

* I pulled out the netwrok cable while i was in nautilus (browsing a samba share), when I went to click on the nautilus window, it locked up.. I gave it a minute but it would not do anything. so I logged off and on  again.

* when I press on help, there is references to Gnome 2.14... is this a bit old?

Other then this Im really happy with at. none of the problems are a big deal for me and Ill keep ubuntu on this Mac.

---

### Post by cyberdork33 on 2007-09-06
First, you probably understand this, but you are using an unfinished version of Ubuntu, so there are going to be little quirks (the gtk bug, the gnome 2.14 references, etc.)

There is an iSight how to, and it should work in ekiga if you follow it. There is a problem with it working in gstreamer though, and this is because changes in the kernel have broken how the uvcvideo module works. There is new work being done to fix it.
**[ HOW-TO: iSight setup]("http://ubuntuforums.org/showthread.php?t=491381")**
**[ MacBook iSight (uvcvideo) bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105638")**

Adding the touchpad config by default is a good idea, but if you ask me, the ones available don't come come to harnessing the power of the synaptic driver. Most features you will have to edit the xorg.conf file for anyway. You can make feature requests on the developer mailing list: **[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel)**

The volume controls are ALSA bugs. It is a different slider for different systems. It is quite annoying. If anyone knows where a bug report has been started, or can help get needed info to the developers, let me know and I will glad to start a bug report on this myself.

I do not have a Macbook, but I know there was a method that should make brightness work. This is for the Santa Rosa machines, but may be your best bet. [http://ubuntuforums.org/showpost.php?p=3224984&postcount=214](http://ubuntuforums.org/showpost.php?p=3224984&postcount=214)

The samba browser / lose network connection is a nautilus bug. It has been like that since I can remember. Usually, if you wait awhile you will eventually get an error message.

---

### Post by ideasman42 on 2007-09-06
Thanks, pommed was in the repo, installed and works a charm (another example of a possible default?)

yeah, was totally ok with installing a beta, the main functions I got the laptop for work fine and I can put up with some quirks for a while. also wanted to help out testing if possible.

---

### Post by cyberdork33 on 2007-09-06
The problem with making it default is that it is strictly a MacBook (Pro) application. Therefore, it is highly unlikely to make it into the default install unless there is a Mac specific installer...

---

### Post by ideasman42 on 2007-09-06
Im tossing up weather this was a reasonable request. and I think it is ;)

However people not running mac's wont need it of course, so the best option might be to check if the user is running a mac and only install it then, same goes for synaptics touchpad drivers (laptop spesific)

On the flip side, installing by default isnt too bad, when you think of it you already get loads of kernel modules and Xorg video drivers for hardware the computer your running will never have.

in more general areas, ubuntu comes with palm-pilot bu default... you see what I mean.

The programs to operate the touchpad and keys are quite small a few 100'k, so I think its reasonable to either install by default or check the hardware and install.


Maybe ubuntu could have an option when installing - Choose your PC - Laptop/Desktop... and for each option it notes the estra software youll have installed. though thats a longer term approch.

The good thing about installing by default is that It Just Works

---

