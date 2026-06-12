---
title: "Tracking Down Errors in Configuration under Feisty"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by tgbrowning on 2007-08-17
I've got some sort of weird erros in my set up and I'm not sure how I can go about checking things out. What files, where, hold configuration data, particularly those for ndiswrapper, networking, wifi, usb devices and cdroms? What programs in the terminal can I run to see exactly what stuff is successfully seen by my system?

If I do nothing to try and install a wifi device, ignore it and only use an ethernet cable directly connected to my router, the system works pretty okay with no overwhelming weirdness.

I'm convinced after about two weeks of trying that I've got something basically screwed up in these areas, and it seems to be at least partially due to repository conflicts and module clashes of some sort. Awhile back, I was getting error messages about usb device files not being present or screwed up.

How-Tos that cause no problem for the vast majority of users foul up my machine royally (how-tos for ndiswrapper/wifi installation, WG111T USB dongle installation and ndiswrapper set upm for example). Side effect examples:  network manager and gedit refusing to close, usb drives refusing to unmount, usb drives refusing to mount suddenly, when they had been mounting with no problem before.

I've been forced to reinstall about a dozen times now, to get shed of a bunch of the error messages. 

I'm fairly stubborn about things, but this is starting to get me down.

Browning>>>

---

### Post by Hobo Joe on 2007-08-17
The bulk of hardware configurations are located in the xorg.conf file:

```

sudo gedit /etc/X11/xorg.conf

```

---

