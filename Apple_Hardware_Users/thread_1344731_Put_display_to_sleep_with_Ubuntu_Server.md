---
title: "Put display to sleep with Ubuntu Server"
date: 2009-12-03
forum: Apple Hardware Users
---

### Post by mattimus13 on 2009-12-03
I have recently installed Ubuntu Server 9.04 for PPC on my iMac G4 1Ghz Flat Panel. It has a NVIDIA GeForce4 MX video card.

Everything is running fine, but I can not figure out how to put the display to sleep.

I have tried installing xset... but when I use the command "xset dpms force off" I receive back "xset unable to open display".

Is there any way I can get xset to recognize the display -or- any way at all to turn off the display? I am using this as a server, mainly SSHing to control it, so the display is pretty much useless for me.

Thank you in advance.

---

### Post by critic on 2010-01-20
I'm having the same issue with a Powerbook G4 running Ubuntu 9.04 server edition for PPC -- I can't find any way to turn off the display.

---

### Post by ironjaw33 on 2010-02-01
I am running the server version on a 1st gen Macbook as a personal web server.  I, too would like a command or script to turn off the display since the laptop has no button to physically turn off the display.

---

### Post by drjimmy42 on 2010-06-17
I'm having this problem on my 5.1 macbook as well.  No matter what I set the power settings to in terms of when to put the display to sleep, whether on battery or plug the display never turns off.  Any thoughts?

---

### Post by Maletor on 2010-07-17
Checkout laptop-mode-tools.

In /etc/laptop-mode/conf.d there is a wealth of power saving goodness in there including an option to put the display on standby (aka 'xset dpms force standby')

---

