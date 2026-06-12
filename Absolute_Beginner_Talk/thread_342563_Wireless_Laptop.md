---
title: "Wireless Laptop"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Duppy on 2007-01-20
Ok installed Edgy on my Fujitsu-Siemens laptop.

It has wireless, and at the minute, is connected to "lo" which I presume is my loopback connector or something. I cannot connect to the internet on it at the minute.

How do i get support for the wireless card?

---

### Post by EdThaSlayer on 2007-01-20
If you want to check if you can connect to other networks you should try going to:
System->Administration->Networking
and then you go to the properties of the "Wireless connection" and check the network name(maybe you have already found out about this since you know the network to which you are connected to)

When that fails, you should try using the Ndiswrapper,which can be found on:
 [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

and if that doesn't work just click [here]("http://www.ubuntuguide.org") and search for "Ndiswrapper".
You will need the original driver cd for that(the website will explain the rest).

---

### Post by mikewhatever on 2007-01-20
Installing Gnome Network Manager might help.

```
sudo apt-get install network-manager-gnome
```

you'll get the icon in the panel after a reboot.

---

### Post by Duppy on 2007-01-20
but i cant connect to the internet on that laptop, so therefore i cant download that can I?

Or shall i plug my ethernet from my PC into it to do it?

---

### Post by mikewhatever on 2007-01-20
If your Ubuntu PC has no internet connection of any kind, check this thread for installation info: [http://ubuntuforums.org/showthread.php?t=286188&page=2](http://ubuntuforums.org/showthread.php?t=286188&page=2)

---

### Post by mlsestak on 2007-01-20
I'm just starting ubuntu myself (though I have years of general Unix experience).  I have an older Dell notebook with builtin ethernet, a Netgear WG511T wireless card and I am running Ubuntu 6.10 (Edgy).  Wireless worked for me out of the box, but only for an unsecured network.  After backing and forthing through various forum topics and reinstalls (since my wireless network uses WPA and no broadcast ESSN, I thought wireless wasn't working at all for quite a while), here is what got everything working for me (I'd like to credit the forum threads/writers that were the most helpful, but I've lost track of most of them).

First, if your notebook has an ethernet connector, connect the cable and enable the connection by going to the menu System > Administration > Networking.  There, click on wired connection and properties and enable connection and your wired connection should be working.

Once that is working, you should probably do an update (it may come up automatically, but the update manager is at System > Administration > Update Manager).

Then you should add network-manager-gnome to your system (for my system, at least, the default System > Administration > Networking could only connect to unsecured wireless networks).  You can hunt this package down using the default Applications > Add/Remove, or the more elaborate System > Administration > Synaptic Package Manager, but from a forum thread I found the simplest method is to type in a terminal window

sudo apt-get install network-manager-gnome

After the package is installed, go back to System > Administration > Networking and disable your wired network, disconnect the cable and restart your machine.  

Once the machine is back up there should be a new icon on the Gnome bar at the top of the screen that looks like the default network icon but kind of with a shadow around it.  Click on that and you should see a list of available wireless networks.  Voila!  If your network is on the list, select it and a configuration dialog will appear.  If your network, like mine, does not broadcast its ESSID, go down the list to the "other networks" item and a enter all the configuration information there.

Once I had all that working I removed the default networking icon (not the network-manager-gnome icon) from the Gnome bar.  

Now I can connect to my network, switch networks and surf the internet wirelessly with no problems.

---

### Post by Duppy on 2007-01-20
installed network manager, doesnt work. Do i need to install some drivers?
It shows me 3 wireless networks, 2 unsecured, and 1 secured (mine). Does this mean that it is working and I just need help setting it up?

Also, when i tried to put the wep password in, i asked it to save in the keyring, and then deleted the keyring from the keyring manager, but it still asks for the keyring password. How do i sort this out?

---

### Post by Duppy on 2007-01-20
bump

---

### Post by Duppy on 2007-01-20
Well yeah, didnt get much help on this:(  and all the programs are crap, but luckily I found a thread by searching google.

If anyone needs a wireless program that actually works.

**connection-manager**

IT works now, so wireless on laptop! :p

---

### Post by mikewhatever on 2007-01-20
Whatever works for you is the best to use.

---

### Post by Duppy on 2007-01-20
Help me please, my other thread, slow windows an slow scrolling.

---

