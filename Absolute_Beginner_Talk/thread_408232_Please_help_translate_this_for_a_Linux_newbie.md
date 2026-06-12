---
title: "Please help translate this for a Linux newbie"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Dizzydawg on 2007-04-13
I found this and i think it can help me but i do not understand it...

> Had the exact same problem as you and i got it solved by

1) Switch to onboard graphics and install ubuntu (if dosnt work try acpi=off)
2) Boot into ubuntu under onboard graphics and run the envy script - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
3) to install the envy script you need module assistant which you can get from here - [http://packages.debian.org/unstable/devel/module-assistant](http://packages.debian.org/unstable/devel/module-assistant)
4) After running the eny script open up konsole and type - sudo nano -w /etc/modprobe.d/blacklist
5) add "blacklist agpgart" and "blacklist intel_agp" at the bottom
6) press ctrl x to exit and save
7) Now type in - sudo gedit /etc/modules
8) Add nvidia to the bottom, save and exit.
9) Now type in - sudo gedit /etc/hotplug/blacklist
10) Add "agpgart" and "intel_agp" to the bottom
11) Save and exit

Now the fun begins in editing the x.org file

12) open x.org - sudo nano -w /etc/X11/xorg.conf
13) Find the section device that lists your graphics intel graphics card
14) Make that section look like this
"Section "Device"
Identifier "GeForce FX 5500"
Driver "nvidia"
#BusID "PCI:1:9:0"
Option "NvAGP" "1"
Option "RenderAccel" "true"
EndSection

15) Find the section below that says "Screen"
16) Edit the Device row that currently lists your intel integrated card to "GeForce FX 5500'
17) Save and exit "ctrl x"
18) Reboot and change the bios to nvidia graphics card
19) Pray and hope that ubuntu loads properly
20) If dosnt then run - "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by justleen on 2007-04-13
which step is not clear?

---

### Post by Dizzydawg on 2007-04-13
everything except #2 and #11

---

### Post by Jussi Kukkonen on 2007-04-13
I think you should explain your problem and hardware and what you are trying to accomplish (if you've done this in another thread already, feel free to link to that discussion). I'm a bit hesitant to just help you with these instructions without understanding the situation: The instructions involve e.g. installing a package from debian by hand. That may be prefectly safe, but often it's asking for trouble...

Then you should probably explain which parts of the instructions are latin to you... it's very hard to know it from this end :)

EDIT: 
> everything except #2 and #11
 dizzydawg, sorry but that's not enough -- you shouldn't expect us to write step-by-step instructions for you without you giving us any information. Please go through the list, explain what is the problem with each one if you want help. Don't take this the wrong way: I'm not trying to discourage you, I do want to help. I also expect you to spend a little time to make it easier to help you. 
About #1: selecting onboard/external graphics card usually happens in the BIOS.

---

### Post by Dizzydawg on 2007-04-13
My problem is that when I try to load Ubuntu, Kubuntu and Edubuntu, Puppy, Fedora, or other linux they say Unknown interrupt or fault at EIP XXXXX", The XXXXX is a number I did not write down. Then My PC reboots itself and goes back to the CD menu. I have tested my memory, I have changed my bio's and ect. My Processor is a Celeron 325. I have 256 mg RAM, and three HDD's two 30gb, and 150gb. I want it installed on the 30bg HDD. Which I emptied and partitioned. Also I am running Windows XP on the second 30bg HDD.

---

### Post by Jussi Kukkonen on 2007-04-13
Can you link to where you found the instructions above -- I don't understand how they are related to your situation?

---

### Post by Jussi Kukkonen on 2007-04-13
This is the bug, I believe:
[https://launchpad.net/ubuntu/+bug/71594](https://launchpad.net/ubuntu/+bug/71594)

You should try the "alternate" installer -- at least if the bug and the hardware sounds like what that bug is about.

---

### Post by Dizzydawg on 2007-04-13
How do i get the alternate Installer?

EDIT: I found it. thank you... i'll edit with the results.

---

### Post by Dizzydawg on 2007-04-14
The Alternative install didn't work.

---

