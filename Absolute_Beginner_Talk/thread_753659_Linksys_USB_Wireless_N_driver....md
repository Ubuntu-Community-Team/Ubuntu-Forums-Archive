---
title: "Linksys USB Wireless N driver..."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Csylleste on 2008-04-12
I have recently installed Ubuntu, but have been fighting with my wireless card to try and get online.

I have already installed the driver using ndiswrapper and double-checked to see if the card is registering with ndisgtk. However, the card is still not registering with the system as being a working wireless device.

Linksys does not provide any Linux drivers, so that is a no go. Does anyone have any suggestions on how to get the card to register as a wireless network device? Or anything that can force it to work through the system?

---

### Post by ritdude on 2008-04-13
Can I have the model of the card?
Also, what type of encryption are you using, if any?
 
(Ironically, I just spent the past 15 minutes getting a WUSBN300 working, so I should be able to help when I get the above info.)
 
 
I'm gonna be MIA all of today, so I'm just gonna give a generalized guide and hope it helps.
 
Linksys doesn't give linux drivers with their Draft-N products, but they package the windows drivers in a way that they can be easily used for linux. Go to the Linksys site and download your driver for windows. After you unpack the folder (unzip it) you should see a bunch of files and folder; the one we are interested in is "Drivers". Open it up, then open up the xp_2k folder (or some varriation of that - mainly just looking for the windows xp driver, not the vista driver). In here you should see a few files. There should be one file ending in .inf and another ending in .sys These are the two files you want. Open ndiswrapper in a terminal and open them to the folder with the .inf and .sys files in them. Type the following command: ```
sudo ndiswrapper -i <name_of_inf_file.inf>
sudo ndiswrapper -l
``` Hopefully you see something like this:
 
<inf file name. : driver installed
device (<device id>) present
 
If you see something like that, enter the following code: ```
sudo depmod -a
sudo modprobe ndiswrapper

```
 
From there, you should be able to get on using KNetworkManager (other programs might work also, I just know that this is the program I use)
 
if you have trouble with ndiswrapper or installing the drivers, click on the link in my sig below, it is very clear on what to do and goes more indepth.

---

### Post by Csylleste on 2008-04-15
I have the same model of card as you do. Tried what you suggested and it did not work. I am guessing that I will need to reinstall ndiswrapper using that guide, and then install my wireless card from here. I have an AMD64 processor and need an install to match it.

---

### Post by ritdude on 2008-04-15
How far do you get?  When you try using the lsusb command, so you get something like what is below (you are interested in seeing something that has Linksys next to it):

greg@tehsystem:~$ lsusb
Bus 003 Device 002: ID 13b1:0029 Linksys
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

If you don't see anything like that, then that means ndiswrapper can't find the radio because the computer can't find the radio.  If the above it working, then try this:

greg@tehsystem:~$ ndiswrapper -l
netmw245 : driver installed
        device (13B1:0029) present

You should get something like that which is above.  The name of the driver should be the same as the one listed above (netmw245) if you are using the same radio.  Something to check for here is to make sure that the number in the parenthesis in the second line of this output matches the number next to the Linksys device from the first output.  (Meaning, my radio id number is 13B1:0029.  You can see this number as the same number in both outputs.

If you get this far, then open KNetworkManager and look for the radio's name in the list.  If it isn't there, then just try the two command written in the above post (and also below):

sudo depmod -a
sudo modprobe ndiswrapper

If you are getting any error messages, post them here and I'll try to figure out what is going wrong.

Good Luck.

---

### Post by Csylleste on 2008-04-16
I have followed that guide, and everything looks good with no error messages. By all rights it should be working. However, once I complete the install and verification, I go and open up the Network Manager. When the manager comes up, there is no wireless connection listed, only wired and modem. I am thinking maybe I have the wrong software set.

Also, is the configuration file supposed to have xx:xx:xx:xx:xx listed for the MAC? Mine does and I am wondering if this may also be part of the problem. If so, how can I open up the file and change and save it. The system will not let me do it with sudo, nor can I log in as root...

---

