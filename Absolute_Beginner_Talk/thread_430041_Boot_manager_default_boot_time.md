---
title: "Boot manager default boot time"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by smoaky on 2007-05-01
Just recently installed Ubuntu  onto an external HDD
I also have a dual boot on my internal HDD with XP and Vista.
Linux boot manager at start-up gives me a list of bootable O/S options.
It gives me by default 10 seconds before it auto boots to my highlighted O/S
I want to change the default time before it auto boots. How can I do this?
I am a Ubuntu noob so be gentle with me :lolflag: 

next prob: upon install my screen resolution is set to 800x600. I cannot change it to my preferred 1024x768.It does not give me the option to do so.
How can this be corrected?
Thanks !!!:) 
smoaky

---

### Post by Zalbor on 2007-05-01
For booting: Edit the file /boot/grub/menu.lst (open a terminal and run "gksudo gedit /boot/grub/menu.lst"). Find the "timeout" line and change the number there.

The second: first, try installing better video drivers. If you have an nvidia card try opening synaptic and installing nvidia-glx or nvidia-glx-new. I don't know about ATI cards, sorry.
This should give you a better set of resolutions, as it will be using your video card as best as possible.

---

### Post by smoaky on 2007-05-01
Great Zalbor,Thanks:) 
I'll try that boot solution.
I have NVIDIA GeForce 6150 graphics card so that hopefully should work fixing my resolution.
Keeping my fingers crossed.[-o< 
Thanks again,
smoaky

---

### Post by smoaky on 2007-05-02
Hi Zalbor and all you other helpful Ubuntu freaks like me) ):P 
screen resolution fixed:) 
adjusted boot time to 4 sec,,,THANKS
Only problem I have now is that Ubuntu hates my Logitech wireless mouse ](*,) 
Just whenever it feels like it my pointer freezes up and I'm stuck. I can't do anything but re-boot
Tried removing the usb cable from the mouse transmitter and resetting the mouse...no luck
Anybody having the same problem? It happened when I changed the desktop background and on certain web sites if that helps with any problem solving.:confused: 
Any solution out there would be greatly appreciated
smoaky

---

