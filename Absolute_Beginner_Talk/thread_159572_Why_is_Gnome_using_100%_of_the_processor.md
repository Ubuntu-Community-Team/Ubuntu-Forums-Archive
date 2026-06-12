---
title: "Why is Gnome using 100% of the processor?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Christmas on 2006-04-13
I have Ubuntu installed on a PC with a P4 2800 MHz and 512 RAM. I added a panel applet for System Monitor so I can see how much my processor is used. One of the things I really don't like at Gnome is the way it uses the system resources for accomplishing simple operations, like resizing windows for example. I noticed that when resizing a window, my processor is used 100% and the resizing makes me feel kind of slow. The same thing happens when scrolling in a list or a webpage. Why is that? I mean it shouldn't use the video card for that kind of operations? I don't know so much about the way graphic processes are handled, please take me easy if I asked something stupid.

---

### Post by ProjectGod on 2006-04-13
its slow on mine too. cpu usage spikes to 100 with simple tasks. memory usage remains consistent. but im using a intel cerelon 333 mhz 128 ram prehistoric beast.! :mrgreen: 

its slow but ikinda like the RDP / VNC session over ADSL VPN connection feel! 

can't help you there. with your specs it should be blazing fast! i find that ubuntu is alot slower than win2k or XP on the same computer. which is alright cause all im interested in is the kernel. :D

---

### Post by Sef on 2006-04-13
> im using a intel cerelon 333 mhz 128 ram prehistoric beast.! 

Have you tried xubuntu?  It's a lightweight window manager.

sudo apt-get update

sudo apt-get install xubuntu-desktop

---

### Post by ProjectGod on 2006-04-13
wow! i'm getting quite alot of good info from these forums. usually reading command lines in books just dont cut it cause we humans tend to remember more if something is directly affecting us or if its something were looking for!

sudo apt-get update
sudo apt-get install xubuntu-desktop

a lighter window manager? sounds great i'll try it.

cheers.

---

### Post by ProjectGod on 2006-04-13
devil@ubu:~$ sudo apt-get update
Password:
Reading package lists... Done
devil@ubu:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xubuntu-desktop
devil@ubu:~$

dont mind me asking but what does the first line do?
it asks for the password... is it the root password?
what about the second line? what does that do?
what is the error message? can't find xubu... does that mean the connection to the mirror site is unavailable the servers are down????

cheers.

---

### Post by Kimm on 2006-04-13
The password it is asking for, is the same password that you enterd during install (the password for your user)

> 
Reading package lists... Done
Building dependency tree... Done


Thats just the package manager going through all the available packages, nothing to think much about...

> 
E: Couldn't find package xubuntu-desktop


APT doesnt seem to be able to find xubuntu, you need to active the repository for that one.
fire up your terminal and type this:

sudo gedit /etc/apt/sources.list

then remove the "#" from every line that has **just one** of these.
Now save and exit gedit, then type this in the terminal:

sudo apt-get update
sudo apt-get install xubuntu-desktop

Hope it works for you now! :)

---

### Post by Sef on 2006-04-13
you can also enable resources by following this link below:

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by ProjectGod on 2006-04-14
great! hope it helps out christmas as it did me. 

cheers.

---

### Post by threegremlins on 2006-04-14
hey just so you know I downloaded the xubuntu iso and loaded it onto my amdk6 450 256mb box and hey great it performs faster than gnome but it still uses memory and has a few other odd quirks like freezing while it's processing. also if your use to the convenience of setting things up the gnome way, then prepare yourself for a little mental work out.

---

