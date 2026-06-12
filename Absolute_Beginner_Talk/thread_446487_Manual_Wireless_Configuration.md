---
title: "Manual Wireless Configuration"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by coarse.sand on 2007-05-17
I'm a newbie to Linux, but I just got through getting my Broadcom 4318 wireless adapter working on my Compaq R4000 (followed the 4318 fuide here on the forums), and everything seemed fine. Ubuntu was displaying it's standard network selection screen, including my wireless router and a signal strength meter. I restarted and was no longer able to connect, and on top of that I went to an option under the network button in the upper right that's left me with nothing but the option Wired Network, which is greyed out, and Manual Configuration I've accidentally done this before and it gets rid of any easily interpreted information about my wireless connections or even how to start a connection. Is there a way to switch back to the standard info window for networks? Connecting to the router is something I can probably fix on my own, but I have no idea what to do with the Manual Configuration window to tell if it's even trying to connect to my wireless.

I just hope there is a way to switch back to the standard view of the networks besides reinstalling Ubuntu and making sure I don't hit manual network config again. Done that once already :)

---

### Post by Ozeuss on 2007-05-17
I'm not sure if i understood your situation, but you might first try to restart dbus:
sudo /etc/init.d/dbus restart

or restart networking-
sudo /etc/init.d/networking restart

but if the problem occurs right after every restart that might not help.
if you're trying to connect to wireless network, you can type "iwlist scan" to see if it catches any wireless networks, or "iwconfig" to see the device status.

---

### Post by coarse.sand on 2007-05-17
Sorry if that wasn't really clear. The normal Ubuntu wireless drop down menu usually seems to show a list of wireless networks with a bar that shows wireless strength, etc. I've somehow done something to the bar so that it shows only a drop down menu with the options "wired network" which is greyed out since I'm not using an ethernet connection, and "manual configuration". My wireless connection fixed itself on a reboot, so that isn't a problem, but the menu hasn't reverted to its normal state, so I have really next to no idea if I'm connected to my wireless outside of loading a website. This is really just a minor GUI problem, but I'd still like to get it resolved if anyone knows how to revert it. Not having the option to select which WLAN I'm on outside of reconfiguring the eth1 option under manual configuration is a pain.



Look of dropdown previously:
_________________________________________
| o wired network (greyed out)
|
|                                        -
|
| o essid of router                signal strength ||||||||||
|_________________________________________
| manual configuration
|_________________________________________


Look of dropdown currently:

__________________________________________
| o wired network (greyed out)
| manual confugration
|_________________________________________


Any trace of available wireless networks has disappeared, as you can see. Any help with this would be appreciated.

---

### Post by SeanHodges on 2007-05-20
If you first check that the wireless driver is installed and working correctly:

1) open up a terminal
2) type "iwconfig"

You should hopefully get a list of network devices, and one of them should dump a load of information other than "no wireless extensions"...

If you get this far your wireless card is still working after your reboot and you just need to turn "roaming" mode back on on your network applet:

3) Click on your network applet (the wireless drop-down menu) and  select "Manual Configuration..."
4) Click on the "Wireless connection" option, ensure it is ticked, and click "Properties"
5) At the top of the dialog that appears, there is an "Enable roaming mode". Tick this and apply your changes

It should be back to normal now, hopefully.

---

