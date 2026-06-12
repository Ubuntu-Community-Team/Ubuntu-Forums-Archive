---
title: "ubuntu will occasionally restart without warning when I close a firefox window"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by b9kline on 2007-07-06
ubuntu will occasionally restart without warning when I close a firefox window. It just slows me down doesn't seem to lose any data. 

Is this a bug? Is it because I tried to install a few programs and was unsuccessful? 

I post here as it is my first post on a linux machine. This is my first successful linux box :D 

thanks,
bk

---

### Post by limbourg31 on 2007-07-06
that is possible, so go into synaptic and try to fix any broken dependencies or type sudo apt-get autofix in the terminal to try and fix everything, and if you want to clean up the machine do sudo apt-get autoremove also

---

### Post by b9kline on 2007-07-06
Synaptic doesn't show any broken packages but I don't think I really know how to find them

I get "E: Invalid operation autofix" when I try the first and I get "E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?" when I try the the second.

I am trying to run a AMD x64 so as to eventually install Cinelerra. I have the 32 bit firefox installed as well now... could that be doing it?

These autofixes and/or autoremove commands would be nice to clean up after my poor attempts at hacking through compiling software when I have no idea what I am doing.

---

### Post by ianaguidiniz on 2007-08-16
I got this same problem using feisty 64bits over vmware. Eventually my X is restarted.

_Config on Firefox About menu_
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

---

