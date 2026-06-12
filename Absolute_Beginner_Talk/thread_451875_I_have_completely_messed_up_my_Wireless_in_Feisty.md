---
title: "I have completely messed up my Wireless in Feisty"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Bright Hammer on 2007-05-22
Hello all I have completely messed up my Wireless in Feisty. I am looking for a way to start from scratch installing my wireless. Here is the series of events.

1.	I Installed Feisty on my Acer 3000 and it worked great except for wireless.
2.	I searched the forums and followed instructions to install wireless for a broadcom 4318(the instructions had me download a script which I ran and my wireless worked)
3.	I was getting really bad signal strength even when right next to the wireless router. 
4.	So I decided to fix it. I did some more searching and I tried wicd
5.	That worked for a little bit but was not as user friendly so I switched back to network manger.
6.	That is when things went wrong. Me being smart decided to update the some files manually without first backing them up. ( I don’t remember the name of the files right now but it had to do with my networking devices.)
7.	That is when everything went wrong. Now I can see the network and the signal strength is excellent but I cant connect to the network. (I am not running any wireless encryption at this point for testing)

I am asking for help to get this resolved. I just want to know what files I can edit to start this process from scratch. Any help would be appreciated.

As a side note: Where is there documentation on where critical files are and consequences of editing them.

---

### Post by Martin on 2007-05-24
can you ping your router or anything? Did you perhaps edit your proxy/DHCP/IP settings? You could do a search in synaptic for anyh=thing to do with wireless networking and mark it for complete removal and then reinstall it.

---

### Post by AZzKikR on 2007-05-24
Usually with networking, the file being edited (by either you as a user, or using an application) is the file
```
/etc/network/interfaces
```
This file contains information on how to connect using your various available adapters (eth0, ra0, wlan0, etc.), when the initialization script
```
/etc/init.d/networking start
```
is invoked.

Try these commands for extra information about wireless, your network and all that stuff:
[LIST]
[*]**iwconfig** - wireless config options
[*]**iwlist** - for checking status of your network, scanning ssid's etc.
[*]**ifconfig** - general interface configuration
[/LIST]

---

### Post by Bright Hammer on 2007-05-29
Thanks for your help. But I think I will just rebuild the laptop. I am having other problems too that I can’t seem to figure out. But I have tweaked with the Laptop quite a bit and I think a rebuild would be best. :(

---

