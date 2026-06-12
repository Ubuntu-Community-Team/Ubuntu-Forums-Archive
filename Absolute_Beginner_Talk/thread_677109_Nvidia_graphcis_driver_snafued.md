---
title: "Nvidia graphcis driver snafued"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by moonfriedpotatoes on 2008-01-24
I used envy to install the nvidia geForce 4200go driver.  everything seems to be working.  xorg.conf shows that the driver is recognized. and the nvidia settings dialog is available.  however, when i look in the restricted drivers menu, the driver is disabled.  when i enable the  driver then restart, my resoultion is reduced to 640x480 until i use the terminal to reconfigure xorg.  #sudo dpkg-reconfigure -phigh xserver-xorg    once i do that the resolution is fixed but the driver is still disabled and so i cannot run any visual effects.  even when the driver is enabled and the box is on 640x480 res i still cannot activate visual effects.  what should i do to rectify this.  my experience is limited but i can follow directions well.  thanks

---

### Post by wolfen69 on 2008-01-24
it would seem to me that the driver is not compatible with your card. you might want to go to nvidia,com and download a legacy driver.

---

### Post by FuturePilot on 2008-01-24
I've seen a number of people have this problem. For some reason the Restricted Driver Manager thinks the driver isn't installed if you use Envy.  The reason why your res gets messed up is because when it installs the one from the repos you have a kernel module mismatch which messes up X. Though I haven't seen a solution to getting Envy and the Restricted Driver Manager to play nice.. :confused:

---

### Post by moonfriedpotatoes on 2008-01-24
balls.  what if i uninstalled envy and all the drivers (i have the legacy driver now) and started afresh, not using envy?  how would i go about doing that?  if someone could hook it up with the terminal code that'd be great.

---

