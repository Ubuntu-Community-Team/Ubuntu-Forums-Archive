---
title: "Finding Correct Developmental Libraries"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-01-16
I am trying to install teh Accordance Bible Program but I ran into some installation errors.  After emailing their support I received the following:
-------------------------
The error is related to not having certain libraries installed that you
need. You need some development libraries.

Here is a list of them:

devel/pkgconfig
required libraries: x11/XFree86-4-libraries, audio/esound,
devel/glib12,
x11-toolkits/gtk12

My suggestion, since you are a newbie to Linux is just to do a full
installation of Linux. That is what I usually do. It will take up more hard
drive space, but not that much.
-----------------

Where do I find these development libraries in Ubuntu 6.10 -- I've checked the Synaptic Package Manager but as the  files in the list do not list these individual pieces I am not certain what to install.  Do I simply install all the packages under "Libraries Development" or can I be a bit more selective?

---

### Post by 23meg on 2007-01-16
Try installing the following: esound, esound-common, xserver-xorg-dev, libglib1.2-dev, libxt-dev, libgtk1.2-dev

---

