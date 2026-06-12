---
title: "Learning Linux"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by emodo on 2005-07-09
Hello!

Ubuntu works excellent on my Averatec 3220 laptop, EXCEPT the wireless. I have a rt2500 wireless card and although there are dozens (literally) of posts mentioning it, and even a wiki guide to installing it, I cannot get it to work.

The problem is knowledge. To install the driver I have to do a bunch of work in the terminal, the problem is that I dont know ANYTHING about the commands. This might seem ridicously, but for the first 3 hours I was typing "$make" instead of "make" because I was following the directions literally.

The main snag I am having right now is this this wiki guide:

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo)

I can go through the first 5 steps fine (Installing the RT2500 Driver), but I cannot complete step 1 or step 2 in the second set of steps (Installing RaConfig, and using it).

Here is the first step I am having problems with:

> 1. To install the utility, you'll need to download and install the kdebase and qt3 development packages. Type:

sudo apt-get install kdebase

note that if you're using Kubuntu, you need not install this package.



I have no idea if I am using kdebase of Kubuntu, I don't even know what they are! Do I need to do this step? When I try it says it cannot find the kdebase.

Just in case I didn't have to do this step I tried the next step:

> Also type:

sudo apt-get install qt3-dev qt3-dev-tools

If qt3-dev fails to install, you might try libqt3-dev - see the comments at the foot of this page.  

I have tried:

sudo apt-get install qt3-dev qt3-dev-tools
sudo apt-get install libqt3-dev qt3-dev-tools
sudo apt-get install qt3-dev libqt3-dev-tools
sudo apt-get install libqt3-dev libqt3-dev-tools

but all of them return saying:

Reading package lists......Done
Building Dependency Tree......Done
E: Couldn't find the package libqt3-dev

Hoping I didn't need to install raconfig I moved onto the 3rd set of steps and I think I completed those correctly.

I went to the network connection window and I see my wireless card there, I set it up and activiate it, but when I try to go to a website, it cannot find it (I am assuming it is infact not connected to the network).

I am hoping to get raconfig installed and that this will let me connect to a wireless network.

I have two questions

1. Do you have any solutions for the those two questions I mentioned above? What am I doing wrong?!??!

2. Do you know of a good book for a absolute linux beginner that I can buy? Threre are dozens of books out there but I would like one which (ideally) uses ubuntu as its example distrobutuiion.

HELP!

---

### Post by poofyhairguy on 2005-07-10
Here is the package:

[http://mirror.clarkson.edu/pub/distributions/ubuntu/pool/main/q/qt-x11-free/libqt3-dev_3.3.3-7ubuntu3_i386.deb](http://mirror.clarkson.edu/pub/distributions/ubuntu/pool/main/q/qt-x11-free/libqt3-dev_3.3.3-7ubuntu3_i386.deb)

download it to your homne folder some way and enter this command:

sudo dpkg -i libqt3-dev_3.3.3-7ubuntu3_i386.deb

---

