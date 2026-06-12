---
title: "[SOLVED] Problem with an Optical Mouse"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by RonB123123 on 2006-07-27
I bought an Optical Mouse recently before I installed Ubuntu 6.0.6 and it doesn't work on it. I got a CD with the mouse but I can't use it on ubuntu. Does anyone know how I can use my Logitech Optical Mouse on Ubuntu? Because my Microsoft mouse sucks lol.

---

### Post by Sef on 2006-07-27
> Does anyone know how I can use my Logitech Optical Mouse on Ubuntu? 

Is it a wired mouse or wireless?  If wired, does it plug into a usb or ps/2 port?  Have you something else to stick in the port to make sure it is good?

---

### Post by RonB123123 on 2006-07-27
I'm not sure if it's a USB, but my old mouse connects to the same little slot as the optical mouse. I just looked in the back of my computer and the mouse is plugged into the outlet that says Mouse right above it and that is the only little outlet for that. 

Could this possibly be a software problem? :confused: 

Thanks again.

---

### Post by steve.horsley on 2006-07-27
It's probably a matter of configuring the X server to expect a logitech mouse. Try this... First make a balckup of the file /etc/X11/xorg.conf with this command: > sudo cp/etc/X11/xorg.conf /etc/X11/xorg.conf_backupand then run the X configuration script:
> sudo dpkg-reconfigure xserver-xorgI gather you can accept the defaults for most questions, but the mouse questions are the ones you need to change things. Then restart X by logging out and in again.

If things don't go right, you can get a text prompt by pressing Alt-Ctrl-F1 and restore the original config with the commands
> sudo cp/etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart but it might be worth kaking a note of the contents of hte modified file first - look for the section about the mouse and note what it says after you specified a logitech one. You may be able to manually edit the config file and correct the mouse entry.

---

