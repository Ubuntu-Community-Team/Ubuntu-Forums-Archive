---
title: "Can't run integrated Asus A52J webcam on ubuntu 11.10"
date: 2012-03-16
forum: Assistive Technology &amp; Accessibility
---

### Post by swinthawulfs on 2012-03-16
So, these are my Asus specs:

Asus A42Jr/A52Jr:
CPU Type = Intel Core i5 430M(2.26GHz Turbo Boost @2.53Ghz)/Intel Core i3 330M(2.26Ghz)
Screen = 14&#8243;/15.6&#8243;
Hard Disk = 500GB 5400rpm
Optical Drive = DVD Super Multi
Graphics Card = ATI Mobility Radeon HD 5470
Video Memory = 1GB DDR3 VRAM
Resolution = 1366 x 768
LCD Features = LED backlight
Memory = 2GB 1066Mhz
Memory Type = 204-Pin DDR3 SO-DIMM
Battery = 6-cell lithium ion
Price = Rm3099

(I thought it was best to put it all here)
_[SIZE=4][COLOR=Black]Here's the subject:[/COLOR][/SIZE]_
[SIZE=2][COLOR=Black]
I'm having problems with my integrated webcam (built into the lid of my laptop). 
I can tell it works - I mean: it's functioning-  'cause when I installed ubuntu 11.10, on the option (in the installation process) that asks you if you want to take a picture (to make it as your user image) it was functioning, I could see myself... but I've tried to install cheese in order to open the webcam, but it does nothing... cheese also doesn't work! [/COLOR][/SIZE]

[SIZE=2]So,
I ran the output for **lsusb; lsb_release -a** and **cheese**:[/SIZE]

swintha@swinthawulfs-K52Jc:~$ sudo -i
[sudo] password for swintha: 
root@swinthawulfs-K52Jc:~# lsusb;lsb_release -a
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
root@swinthawulfs-K52Jc:~# cheese
Xlib:  extension "GLX" missing on display ":0".

(cheese:3499): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
root@swinthawulfs-K52Jc:~# 


I seriously do not understand the problem...

I wonder if it has anything to do with me not being able to install the Nvidia drivers?..

[B]Can anyone help me out?
What do I do?[/B]

Thanks, swintha

---

### Post by overdrank on 2012-03-16
Hi and welcome. Please do not create multiple threads on the same issue. Duplicate _[here]("http://ubuntuforums.org/showthread.php?p=11771979#post11771979")_. Thread closed.

---

