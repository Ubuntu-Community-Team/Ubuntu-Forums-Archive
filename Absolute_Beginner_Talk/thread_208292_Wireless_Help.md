---
title: "Wireless Help"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by tennyis on 2006-07-03
Hey guys, 

I am having trouble getting my wireless going, Ubuntu picked up my integrated broadcom card in my Compaq R4000 notebook by default. When I go into the networking devices, if I activate it it will not find any SSID using the wireless assistant. If I try setting the IP manually it comes up with an error and will not activate it. Any idaes?

---

### Post by wolfmaniac on 2006-07-03
u dont have the firmware installed.
ubuntu comes with drivers but not firmware.
juz install ndiswrapper.

refer to a how to in this forum.

---

### Post by MarkSheely on 2006-07-03
Do you know which Broadcom card you have?

--Mark

---

### Post by Jagot on 2006-07-03
If you don't know which card it is then type this command:

```
lspci
```

---

### Post by tennyis on 2006-07-03
Broadcom 4318. 
I did the how to guide for the broadcom cards, and got it somewhat working. At first Network manager would display all of the SSID's that it found and allow me to connect to my one. it gave out an IP, subnet, gateway, etc. However I could not browse any websites. At this point I rebooted my laptop and now I cannot even see any SSID's. 

Linux has a loooooooooong way to go before it can compete with windows in ease of use!

---

### Post by Jagot on 2006-07-03
I have the exact same card.  Some people seem to have got it working with the built-in Broadcom drivers with Dapper, but I always do it through ndiswrapper.

You can get ndiswrapper using the following commands:

```
sudo aptitude update && sudo aptitude install ndiswrapper-utils
```

You'll need to get the Windows driver for your card which you should be able to get from Compaq's website.  The specific file you'll need is bcmwl5.inf.

Here's what I do to get it working (this assumes you've placed the driver in a folder on the desktop):

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

That installs the driver itself.  However, we now need to blacklist the Broadcom drivers that come with Dapper otherwise they'll try and take over and it won't work:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

You'll then need to activate in network settings and fill in any information required.  Then remember to change the default device in the network manager in the top right corner otherwise it'll appear as if its not working - by default it monitors the ethernet connection, so change to wlan0 or whatever it is.

---

### Post by tennyis on 2006-07-03
I did this and it shows that I no longer have a wireless device installed... so now I can't do anything with it. Any ideas on why? Maybe I did something wrong.

---

### Post by tennyis on 2006-07-03
I have blacklisted ndiswrapper when i was doing another one so this is probably why but it keeps telling me that the blacklist file is read only, even tried a reboot... any ideas?

---

### Post by tennyis on 2006-07-03
nevermind fixed that part, still does not show any devices installed now though :( argh!

---

