---
title: "Screen Sesolution"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by wadeall on 2006-10-23
Hi I've just installed Ubuntu Dapper Drake on my system.

I'm using a 20in widescreen Viewsonic monitor which is designed to work best at resolutions of 1680x1050.  When i go to Preferences Scrreen Reolution this doesnt seem to be an option.  Do I need to install anew driver of r something?  My graphics card is a XFX Geforce 7600 GS

I'm using an Opteron 144 Processor and have installed a 64 bit Ubuntu system? Was that a mistake?OWuld I have been better off  installing a 32 butsystem?

Many thanks for any help

Wade

---

### Post by Danny Boy on 2006-10-23
My guess would be you need the nVidia drivers.

This [link]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") from UbuntuGuide.org should explain things to you. 

If that's too complicated install [Automatix]("http://www.getautomatix.com") and have it automatically install the nVidia driver.

Good Luck, :)

Dan

---

### Post by barkej on 2006-10-23
You need the Nvidia drivers.  [Automatix]("http://getautomatix.com") seems to make this very painless.

---

### Post by FriscoSoxFan on 2006-10-23
I'm a serious newbie, so take this for what it is worth. Your problem might not be the graphics intallation, but the monitor not being fully recognized. Check the settings in your /etc/X11/xorg.conf file. This is the help I used to hack mine: [http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html)

---

### Post by wadeall on 2006-10-23
ll Automatix as suggested but got this at the  end:


W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatur es couldn't be verified because the public key is not available: NO_PUBKEY 18B52 FE3521A9C7C
W: You may want to run apt-get update to correct these problems


What is the public key and  where do i get one???

Im very confused already

---

### Post by wadeall on 2006-10-23
OK  I  got utomatix installed now (didnt uncomment all thenecessary stuff)

---

### Post by brummygem on 2006-10-23
After a fraut start, I managed to install ubuntu at 3:30 this morning](*,) :p 

Two immediate problems;

The first is to do with this thread.  I change the screen rsolution by going system - preference - screen resolution BUT it doesn't work?  As soon as I click "make default for this computer" and "apply",  I get a log in window and back to the desktop](*,)  Resolution unchanged:confused: 

Second problem probably needs a new thread but I can't get my email to send.  I can receive OK just not send:confused: :(

---

### Post by wadeall on 2006-10-23
Thanks for the help guys. It seems it was a problem specific to my monitor a Viewsonic 2025vm which necessitatted making sure it was operating at 60hz rather than 75hz. If you have  the same problem there is a how to solve it written by  somebody somewhere.

---

