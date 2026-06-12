---
title: "Can't install wine"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by mavix on 2006-08-31
I downloaded the wine .deb package in windows, then copied it to linix. When I tried to install it by double-clicking on it, the install button was disabled, and had some error message in red text next to the button.
I read that I should type: 
dpkg -i wine*.deb
Will this work?
Please help.

---

### Post by mtn on 2006-08-31
Have you tried installing it with Synaptic (add/remove... at the bottom of the main menu)?

That is the recommended way and should only take a click or two!

---

### Post by XaeroDegreaz on 2006-08-31
Hey bud. Why not get WinE from the Synaptics manager? It does everything for ya :)

System > Administation > Synaptic Package Manager

Then, enter a search for "wine" ( no quotes ;) )

Then mark the one named "wine". Then hit apply. It will download and install all by itself.

I have discovered, in my very few days using Linix, that the Synaptic Package Manager is the way to go when you wanna download something. It has practically anything that you need ;)

You could also run "sudo apt-get install wine" from the terminal.

Good luck!

---

### Post by XaeroDegreaz on 2006-08-31
> **mtn said:**
> Have you tried installing it with Synaptic (add/remove... at the bottom of the main menu)?

That is the recommended way and should only take a click or two!

Haha he got to it just a split second before I hit submit >.<

---

### Post by 3rdalbum on 2006-08-31
Whenever you post a question, please actually tell us what error message it was, rather than just saying "There was an error message". It helps us help you.

I'm guessing that the wine package requires something that is not installed on your system. If you have read the instructions for getting your dialup connection going, go into the Software Properties control panel and enable all the repositories. Then go into Synaptic package manager, press Control-R. When it's finished downloading the information, quit Synaptic and install your Wine package through GDebi.

---

