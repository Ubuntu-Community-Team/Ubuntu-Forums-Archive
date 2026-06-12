---
title: "Need help with ubuntu"
date: 2016-06-11
forum: Apple Hardware Users
---

### Post by Unlawful on 2016-06-11
I have two questions and any answers would be much appreciated!
1. I have ubuntu on a flash drive because it's easier for me to access it that way but I was wondering if I can use my Mac OS gb space for the ubuntu OS also without wiping the mac OS. I can try to discuss this more if you don't understand.
2. I need help connecting to the internet i've tried looking up tutorials but I don't understand them.

---

### Post by RobGoss on 2016-06-11
Hello and welcome to the forum, This tutorial might be what you need to get started for a Mac user [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx) I'm sure for Mac users the install might be slightly different but yet the same concept

---

### Post by Unlawful on 2016-06-11
I mean I have the OS installed but on the desktop I have to install the latest version

---

### Post by yancek on 2016-06-11
Do you have Ubuntu as a Live CD on the flash/usb drive or did you do an actual full install to the flash drive?
If you want to also install to the hard drive of the Mac, you would need to first shrink your partitions on the hard drive of the Mac to make unallocated space on which to install Ubuntu.  You would need to investigate to determine if the machine is UEFI which is quite likely and you would then need to install Ubuntu UEFI also.

It can be done but it will be more difficult than a standard PC as Apple is extremely proprietary.  I've seen sites explaining how to do this over the years but have never used a Mac so can't give you any more info.

---

### Post by grahammechanical on 2016-06-12
> 2. I need help connecting to the internet i've tried looking up tutorials but I don't understand them.

Wired connection (ethernet) or Wireless/WiFi connection?

Here  is the first problem: It is possible to make a WiFi connection when we  are running a live/try Ubuntu session but the connection details will  not be stored permanently. For the connection details to be stored  permanently we need to install Ubuntu to the USB memory stick with  persistence.

Second, problem: The Linux  kernel may not have a driver module for our wireless adapter. And to  install a wireless driver we will need an internet connection as the  driver is downloaded from the internet. This is why it is recommended  that we have an internet connection when installing Ubuntu whether on  the hard drive or a removable drive which is what the USB memory stick  will be used as.

Also, new versions of Ubuntu are released every six months and sometimes  there are changes that affect the instructions on how to do things.  There are also Linux distributions that are built on Ubuntu and people  think that these are also Ubuntu but they are not and things are done  differently in these distributions. This is why we like to know the  version of Ubuntu that you are using.

In Ubuntu 16.04 we can go  to the power/cog menu (the one that lets us shut down) and select Ubuntu  Help. Then we go to Networking, web, e-mail and chat and select  Wireless networking and then Connect to a wireless network and we see  this:
> 

[LIST]
[*]If you have a wireless hardware switch on your computer, make sure that it is turned on. 
[*]Click the [COLOR=#6C6C6C]network menu[/COLOR] in the [COLOR=#6C6C6C]menu bar[/COLOR], and click the name of the network you want to connect to.

If the name of the network is not in the list, select [COLOR=#6C6C6C]More Networks[/COLOR] to see if the network is further down the list. If you still do not see the network, you may be out of range or the network [might be hidden]("xref:net-wireless-hidden"). 
[*]If the network is protected by a password ([encryption key]("xref:net-wireless-wepwpa")), enter the password when prompted and click [COLOR=#6C6C6C]Connect[/COLOR].

If  you do not know the key, it may be written on the underside of the  wireless router or base station, in its instruction manual, or you may  have to ask the person who administers the wireless network. 
[*]The network icon will change appearance as the computer attempts to connect to the network. 
[/LIST]


With  Ubuntu 16.04 a successful connection is shown by the Network Manager  icon changing into 2 arrows pointing in opposite directions. If you do not see any wireless network connection (access) points then either the wireless adapter is switched off or you do not have a wireless driver installed. It is also possible that Networking has been disabled or WiFi has been disabled. 

Information on these matters helps in troubleshooting.

Regards

---

### Post by JayKay3OOO on 2016-06-13
I tried it with my old mac book pro and wasted half a day, loads of guides and never got the mac to load the linux disk that worked fine on Windows and could be read fine on the mac, but just no boot so no ability to run the OS.

---

### Post by howefield on 2016-06-14
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by bapoumba on 2016-06-16
You may find easier to run ubuntu in a VM such as VirtualBox. Some ubuntu releases I have installed and could get most things working. I have not tried recently, it is all so easy to use VB.

---

