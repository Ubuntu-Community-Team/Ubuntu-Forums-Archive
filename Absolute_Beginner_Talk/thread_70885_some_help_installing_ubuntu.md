---
title: "some help installing ubuntu"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by NewGuy00 on 2005-10-01
I am completely new to linux, and I am trying to install Ubuntu onto my laptop. I downloaded the image of the install cd ( the hoary hedgehog 5.04 version), and burnt it correctly onto a cd. Then when I boot my computer with the disc, the installer appears. I push the enter button for the defaults. Then I see a whole bunch of data flashes by, then (when I think the data is finsihed scrolling) it freezes and I get a black screen. 

I have an hp zv6000 notebook with an amd64 processor, and an ati radeon xpress 200m graphics card. I have tried both the 64 and the other 32 bit version for installation, and neither worked. I even tried the live cd, and that didn't work either. In all cases I get a black screen after I say to load the default. I have tried slowing the burn speed, but that didn't do anything either. 

Any ideas how I can install ubuntu?

---

### Post by mlomker on 2005-10-01
A lot of people seem to have [trouble]("http://ubuntuforums.org/archive/index.php/t-36991.html") with that laptop.  You could search on the model number here.  Some people say that Breezy runs better than Hoary did on that machine.

---

### Post by tymek666 on 2005-10-01
First, try linux noapic at boot. It should hepl. Then, after installing you'll have problems with X freezing after login, so you'll have to add NoAccel option under device section in xorg.conf file...

There was a lots of topics about it..

---

