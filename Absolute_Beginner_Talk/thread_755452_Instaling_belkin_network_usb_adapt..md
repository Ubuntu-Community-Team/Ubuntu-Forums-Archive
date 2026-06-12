---
title: "Instaling belkin network usb adapt."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by tosh-tecra on 2008-04-14
I cant seem to figure out how to instal the programs needed to run a belkin 54g wireless network adapter

You see, I have an old laptop which I recently instaled ubuntu 6.06 on.  
I want to be able to get online and instal the latest versoin but I cant get a wireless connection because ubuntu won't recognize the windows setup         ................a little help       I'm a beginer......

---

### Post by estaticd on 2008-04-14
You're probably going to need to connect with a ethernet cable or have another computer with internet connection and a way to install the network drivers for the wireless.  It's a classic "chicken or the egg" moment.

I do suggest following some instructions:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
or
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)
or
[http://ubuntuforums.org/showthread.php?p=40016](http://ubuntuforums.org/showthread.php?p=40016)

Not 100% sure you need to use NDISwrapper since you haven't posted a model number of your USB wireless adapter, but it should work, and is fairly painless.

---

### Post by james_vanb on 2008-04-16
If you have the install cd, ndiswraper should work.  The following installed my Belkin Wireless USB Adapter in Gutsy and has worked for some others with different verrsions:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad - the default for Ubuntu is gedit) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add the following to end of list:

blacklist rt2500usb
blacklist rt73usb

Save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically on my old Dell Latitude, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

Good luck.

---

