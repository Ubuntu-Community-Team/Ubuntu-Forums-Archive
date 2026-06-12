---
title: "[SOLVED] Can't install build-essential in Xubuntu 7.04"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by tiachopvutru on 2007-08-25
I'm not sure if there's any significant difference between Ubuntu or Xubuntu but since I have no internet connection on the machine I install Xubuntu on so I can't do **sudo apt-get update** and my wireless device needs ndiswrapper, I'm trying install build-essential. 

**sudo apt-get install build-essential **can't find anything in the E: drive (probably because the Xubuntu CD is meant for light weight?)

I downloaded the build-essential.deb but it says missing dependency. Either libc6-dev or libc-dev works, except that I can't find a debian package for either of those, only the source code.

I'm looking for either one of the debian packages, or any other ways to get build-essential installed

---

### Post by aysiu on 2007-08-25
> **tiachopvutru said:**
> I'm not sure if there's any significant difference between Ubuntu or Xubuntu but since I have no internet connection on the machine I install Xubuntu on so I can't do **sudo apt-get update** and my wireless device needs ndiswrapper, I'm trying install build-essential. 

**sudo apt-get install build-essential **can't find anything in the E: drive (probably because the Xubuntu CD is meant for light weight?)

I downloaded the build-essential.deb but it says missing dependency. Either libc6-dev or libc-dev works, except that I can't find a debian package for either of those, only the source code.

I'm looking for either one of the debian packages, or any other ways to get build-essential installed
Even though *ndiswrapper* isn't on the CD (God knows why they took it off for 7.04), I think *build-essential* is still there. Try ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by tiachopvutru on 2007-08-25
Thanks, I'm able to install build-essential but now I've run into another problem...

After I was done with setting up ndiswrapper and the necessary drivers. I was trying to install *network-manager-gnome* in the Synaptic Package Manager but it returns to me this error:

```
**Could not mark all packages for installation or upgrade.**
The following packages have unresolved dependencies . Make sure that all required repositories are added and enabled in the preferences.

network-manager-gnome:
Depends: libbonobo2-0 (>=2.15.0) but it is not installable.
Depends: libbonoboui2-0 (>=2.15.1) but it is not installable.
Depends: libgnome2-0 (>=2.14.1) but it is not installable.
Depends: libgnomeui-0 (>=2.17.1) but it is not installable.
Depends: libgnomevfs2-0 (>=1:2.17.90) but it is not installable.
Depends: libpanel-applet2-0 (>1:2.18.1) but it is not installable.

```

Here my problem is this. Having no Internet connection on my Xubuntu computer I went to download the debian packages and transfer with USB memory stick. The libbonobo2-0 .deb needs libbonobo2-common .deb in order to install. So I went to download libbonobo2-common .deb. Thing is, the libbonobo2-common debian can't install either without a dependency. That dependency turns out to be libbonobo2-0 ... Now I'm pretty much stuck. So what do I do now in order to get network-manager-gnome installed? :confused:

---

### Post by kevdog on 2007-08-26
I feel your pain, however I think a much better way to go about it, would be to bring the wireless connection up manually, and then once it was up, install the network manager from repository.

If ndiswrapper is setup appropriately (which is a big if), and you have no encryption at the router (no WPA/WEP/MAC filtering), see if you can first see your router:

iwlist scan

If the router appears, try connecting like this (assuming your wireless interface is wlan0):
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <"ESSID_in_QUOTES">
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by tiachopvutru on 2007-08-26
I would like to do what you say but unfortunately, the wireless router is not mine. It belongs to my householders who live above me. I can only access to the router wirelessly, that's all they let me do (the computer I'm using now is also accessing wirelessly to it) ... Furthermore, there's WEP encryption. I don't think I can ask them to turn it off. We barely communicate.

So I probably have no choice but figuring out a way to install network-manager-gnome. Or at least find a temporary Internet solution. When it's a no go I would probably have to reinstall Ubuntu. I used to run Ubuntu 6.06 on that machine and was about to configure my wireless device. I uninstall Ubuntu for Xubuntu because it ran kinda slow.

---

### Post by kevdog on 2007-08-26
Ok two options for you -- forgot you are running Xbuntu.  Download the WICD deb -- this is "like network manager".  Need a USB stick to make the transfer and then install (general syntax:)

sudo dpkg -i ******.deb

or since you have WEP (and if you know the WEP ascii key)

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <"ESSID_in_QUOTES">
sudo iwconfig wlan0 key s:ASCII_KEY
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

Hey at least Im giving you some ideas!

---

### Post by tiachopvutru on 2007-08-26
Yay for wicd ... It saves all the hassles of trying to install network-manager-gnome. If only I have known this tool sooner... It makes me question the effectiveness of this tool compared to network-manager-gnome though. What I mean is, all that work trying to setup network-manager-gnome, and I would have done it much sooner and easier with wicd. Of course, I don't really think wicd is inferior.

Thank you very much for your help. I have a couple more questions though... How do I set it to startup? Or does it already set itself?

Also, how do I put something on the panel? Add Item doesn't reveal some stuffs I wanna add

---

### Post by tiachopvutru on 2007-08-26
Errr, well, I'm having problem again. Wicd won't connect to the Access Point... It detects it but it won't connect. It did before I rebooted but now it doesn't... When I set a Static IP, though, the program notifies me that it connects, but 0% ...

---

### Post by kevdog on 2007-08-26
Try connecting manually, and the only reason I am telling you this is that you will likely get some debugging messages along the way.  I dont know why you are connecting.  Could be signal strength, wireless configuration, a bunch of different reasons.

---

### Post by tiachopvutru on 2007-08-26
By "manually", you mean I'm to click the "Connect"? It's still isn't connected... When set Static IP, it says "Connected to nicholasnho at 0%" ... When I don't, it tries to connect and for some reason it halts at the part "Obtaining IP Address" ... Yes, the Router is far away but I didn't have any connection trouble when I used to use Windows XP

Actually, I'll create another thread since this question doesn't really fit the thread's name

---

