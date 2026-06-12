---
title: "Having problems installing ndiswrapper"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by M4v3r1ck on 2007-04-06
Ok, so I was given the command by someone who does use linux-

sudo apt-get install ndiswrapper

And I'll enter my password and it says that it can't find the file on the E: drive. 

Ultimately, I'm trying to get my wireless driver to work, and my video card driver. It's a laptop with built in wireless. The video card is an ATI Radeon Xpress 200M.

Any help would be appreciated.
~M4v

---

### Post by Maestro23 on 2007-04-06
Ndiswrapper HOW-TO:Go to the link below and search "ndiswrapper".  You will find several HOW-TO for different wireless cards.
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

For your video card:

ATI HOW-TO: Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Envy script: Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


Good luck.

---

### Post by M4v3r1ck on 2007-04-06
Ok, new prob.

turns out the command was-
sudo apt-get install ndiswrapper-utils-1.8

But now, I go to install the wireless driver and upon installing it the first time nothing happened.

So, I went to uninstall it and it says it's not installed. I view the list of drivers it has and it's there, but it says invalid driver and I can't uninstall it, or reinstall it.

Any ideas?

---

### Post by mi_were on 2007-04-06
> **M4v3r1ck said:**
> Ok, new prob.

turns out the command was-
sudo apt-get install ndiswrapper-utils-1.8

But now, I go to install the wireless driver and upon installing it the first time nothing happened.

So, I went to uninstall it and it says it's not installed. I view the list of drivers it has and it's there, but it says invalid driver and I can't uninstall it, or reinstall it.

Any ideas?

Sounds very familiar. I assume that you typed

sudo ndiswrapper -l

then got a list of the drivers installed like say

mrv8000c

to remove it then type in

sudo ndiswrapper -e mrv8000c

that should solve your problem 

P.S substitute my driver name with your own.

If it fails post the list of command line entries and output then we can have another go at the problem. It should be really easier to fix and quick.

regards

---

### Post by M4v3r1ck on 2007-04-06
Hey, thanx, that worked. lol I must be over complicating things. Either way, so, I have my driver for the wireless. It's a BCM4318, and the file is bcmwl5.inf. It's in a folder.

Trying to install that it gives me the invalid driver again, so I removed it, leaving the question of how dumb am I? And what do I need to do next?

---

### Post by Maestro23 on 2007-04-06
> **M4v3r1ck said:**
> Hey, thanx, that worked. lol I must be over complicating things. Either way, so, I have my driver for the wireless. It's a BCM4318, and the file is bcmwl5.inf. It's in a folder.

Trying to install that it gives me the invalid driver again, so I removed it, leaving the question of how dumb am I? And what do I need to do next?


You tried the steps similar to these: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29)

---

### Post by M4v3r1ck on 2007-04-06
Ok, so I tried the examples and that didn't work either. I'm still getting the invalid driver command.  Any other ideas?

---

### Post by mi_were on 2007-04-07
> **M4v3r1ck said:**
> Hey, thanx, that worked. lol I must be over complicating things. Either way, so, I have my driver for the wireless. It's a BCM4318, and the file is bcmwl5.inf. It's in a folder.

Trying to install that it gives me the invalid driver again, so I removed it, leaving the question of how dumb am I? And what do I need to do next?

Okay you have your driver in a folder and u know its location. (I personally put my drivers on the desktop because I now know the path by heart format included!).

Anyway just to make sure u have the path right, use the terminal and change directories to the one holding your driver and list the files in that folder. If your driver is listed then you have the path right.

Next using the sudo ndiswrapper -i command add the path and the driver and enter. Example below

$sudo ndiswrapper -i /home/michael/Desktop/driver/bcmwl5.inf

you should have no error messages and the driver should be properly installed.

---

