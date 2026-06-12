---
title: "ATI Restricted Driver"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-23
Hi,
why is it that Beryl does not work with the ATI Restricted Driver enabled??
I just installed PlaneShift and the game works fine only with the Restricted Driver Enabled, but Beryl does not work with it.

So when I want to play the game I have to enable the driver and when I don't and want to run Beryl as a desktop manager I need to disable the driver.

Why? The Restricted Driver is for 3d Acceleration right? Why doesn't Beryl work with it?

---

### Post by Kubunteando on 2007-06-23
Beryl can work using to ways of using the 3D desktop:

- AIGLX
. XGL

AIGLX is the default used in Ubuntu. I guess you are using this one.
So the restricted ATI drivers do not support AIGLX, but the Open Source do.

So you have to use XGL instead together with the restricted drivers to use Beryl.

Check the forums or the Beryl homepage for the combination: ATI + XGL + Beryl.

---

### Post by videocheez on 2007-06-29
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

The guide at the above URL worked great.

---

