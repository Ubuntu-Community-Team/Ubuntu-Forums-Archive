---
title: "install external modem from cd"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by reecedeg on 2006-11-30
I am very new to linux and very old otherwise. I need help getting my external modem software to install. I have tried Synaptic pkg.mgr. and read a lot of instructions including some terminal sudo commands and can't get the cd to run.Please help? Thanks -R:

---

### Post by polly1 on 2006-11-30
Hi and welcome

To  help you, can you post the Make and Model number of your modem and whether it connects to a USB port. We need this information because very few companies issue USB drivers for Linux. 

The installation CD is meant for Windows and will not work on Linux, hence my request

---

### Post by reecedeg on 2006-11-30
Zoom model 3049  It is a serial modem.The box says it works w/ linux and I see a gnome footprint icon as part of the file. I cannot get setup.exe to start. Thanks so much for your help. R

---

### Post by PennYanPete on 2006-11-30
Hi reecedeg

First, .exe files do not work in linux.

Try this...system-admin-networking 
you should see network settings and modem connection. Click on modem connection and then properties. You need user name, password, and isp phone number. For modem port, select ttyS0. Under options, tic set modem as default and use provider nameservers-click ok

Click activate and your modem should dial

PYP

---

### Post by Bartender on 2006-11-30
Before you follow the above instructions, turn the PC off, then turn it back on with the modem connected and turned on. With 6.06 there's an auto-detect button in the modem setup that will find which serial port the modem is on.  Very nice feature.  I noticed this is gone with 6.10, and it's not there with Xubuntu either.  If you don't have the auto-detect, try tty/dev0 if the modem is connected to the upper serial port.  My USR external has about 7 or 8 little tiny dipswitches that control the modem's behavior.  Does the Zoom also have a bunch?

---

### Post by reecedeg on 2006-12-03
Thanks everyone. I am on line and downloading package files. I was so hung up on the cd that I hadn't tried to just run the modem. I had one hiccup. I filled in the area code for my dial up connection and it would only dial that until I deleted the area code I had filled in one of the blanks. The Zoom has a number little switches on the front w/ explain on bottom. I sure thank you all. reecedeg

---

