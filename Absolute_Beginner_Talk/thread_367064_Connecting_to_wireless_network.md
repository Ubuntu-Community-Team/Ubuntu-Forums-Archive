---
title: "Connecting to wireless network"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Janzomaster on 2007-02-21
Hi, I just installed Ubuntu and now am trying to access the internet through my wireless card.

The wireless card works fine, Ubuntu connected to a wireless network, to one of my neighbours which isnt secured. Now I downloaded the the wifi wireless network whatsoever program to be able to choose my network. First, I disconnected myself from the neighbours one and then tried to connect to mine. Didnt work. Says "retrieving ip address" then its not connected.

The worst: I couldnt connect to my neighbours network anymore, not even after deinstalling the wifi network chooser program, so I had switch back to my windows installation...

Now, how do I connect myself to my network through the standard ubuntu network configuration utility. Is there a way to get some kind of reaction to the connection attempt? I hack in the details, the key etc. and hit ok, he says hes applying the changes and then nothing. I need a debug reply to work on the problem!

---

### Post by Strider on 2007-02-21
Use the iwconfig program from the console/terminal to try connecting.  I would also disable any WEP/WPA you have on your AP first to verify you can connect and then re-enable.  This way you'll verify if it's a problem with the card/driver or if it's a problem with the WEB/WPA keys.

-Mike

---

### Post by jpeddicord on 2007-02-21
To add to Strider's post:

To find the name of your wireless device in Ubuntu, just type `iwconfig` in a terminal window. It will list some devices, and next to them it will list if they are wireless or not. Look for the device that does not say "No wireless extensions."

Next, take that name and replace <name> with that in the following terminal command:```
iwconfig <name> essid <network name>
```To find the network name, or to scan for available wireless networks, just run```
iwlist <name> scan
```

Jacob

---

