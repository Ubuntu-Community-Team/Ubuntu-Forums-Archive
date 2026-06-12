---
title: "Clear out previous drivers"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by newlinuxuser on 2006-02-21
Ok i've found the correct driver for my wireless card even though there seems to be alot of problems with it and linux I want to give it a shot. what are the steps I need to go through to remove failed attempts of installing drivers and setting up a wireless connection and seondly properly install my driver and get connected :confused:

---

### Post by aeiah on 2006-03-01
i cant help with this but im bumping it up because id find it really useful to do a fresh install of my wireless drivers. anyone care to help? 

thanks

---

### Post by peabody on 2006-08-21
Okay, to get it working you need to use something called Ndiswrapper.  You can get it by installing the packages ndiswrapper-utils and ndisgtk.  You do this by opening a terminal and typing:

sudo apt-get update
(wait for it to finish)
sudo apt-get install ndiswrapper-utils ndisgtk

It'll ask for your password, which when you type it won't be repeated.  It may also ask you if you wish to continue.  You may need to reboot once after it has been installed.  If everything has gone to plan, there should be a new menu item in the Administration (System?) menu that says something like Windows network drivers.  Select that, enter your password, and try and install the driver via the *.inf file from within that dialog.

---

