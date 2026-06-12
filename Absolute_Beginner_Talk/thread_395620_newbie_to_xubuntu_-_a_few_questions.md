---
title: "newbie to xubuntu - a few questions"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by olileauk on 2007-03-28
well, first off, I'm a new Linuxer. so I don;t know a lot about it.
I have xubuntu because my laptop is ooold, and i'm running 7.04 Feisty

I have a wireless dongle (Belkin F5D7050) and it's detected by xubuntu, yet i cannot seem to work out how to connect to a network. I;ve gone through applications > system > network and set all those values up within network settings, but that doesn't seem to do anything. I know on ubuntu there is a package which allows simple connection to a wireless network, and may go to ubuntu (and deal with the performance and battery life decrease) if there's no way to do a similar thing on x.

I've set up the network monitor on the top bar, and every now and again i get some response from the "data out" bar, but if i try to use the 'net, nothing happens.

this is rather frustrating.

Thanks for any help.

---

### Post by dstew on 2007-03-28
What is the output of **iwconfig**, entered on the command line?

---

### Post by olileauk on 2007-03-28
> **dstew said:**
> What is the output of **iwconfig**, entered on the command line?

for wlan0:
IEEE 802.11g ESSID:"Leanet" (my network)
Mode: Managed Frequency:2.462 GHz Access Point: 00:0D:0B:5E:D3:8A
RTS thr: off Fragment thr=2346 B
Link Quality: 0 Signal Level: 0 Noise Level:0
Rx invalid nwid:0 Rx invalid crypt: 0 Rx invalid frag: 0
Tx excessive retries:0 Invalid misc: 0 Missed beacon: 0

---

### Post by igknighted on 2007-03-28
You need to get either wifi-radar or network-manager for wifi.  The default networking app was built before wifi was popular, and while they tried to tack it on, it's really hit or miss.

So with the wifi dongle plugged in, type "lspci" into the terminal and post the result here.  This way we can identify your chipset and tell you if you need additional drivers.

Finally, what type of encryption (if any) are you using?  WEP should be no problem, but if you are using WPA or WPA2 there will be more work involved.

---

### Post by olileauk on 2007-03-28
I'm not using any encryption (to save hassle until i get this working)

the wireless dongle is external and USB, and doesn;t appear in the lspci command. there are linux drivers for it, because on ubuntu (before i switched to x) i could connect to certain networks fine, and also i know it uses a ralink rt2500usb driver
as X is built on the ubuntu base, i assumed drivers are the same...

where would i get wifi-radar and/or network-manager?

---

### Post by igknighted on 2007-03-28
try synaptic, they both should be there.  Or from a terminal:
```
sudo apt-get update
```
then
```
sudo apt-get install wifi-radar
```
or
```
sudo apt-get install network-manager
```

---

### Post by olileauk on 2007-03-28
I, uh, don't have the internet. so I can't actually use that method, and they're not on the disc. there's not a way to download them onto another pc and transfer them across is there?

if they're on the ubuntu 7.04 disc, i can re-burn that and stick it and and get them from it.

---

### Post by igknighted on 2007-03-28
> **olileauk said:**
> I, uh, don't have the internet. so I can't actually use that method. there's not a way to download them onto another pc and transfer them across is there?

There is but its tedious.  It would be better if you could plug in until wireless is set up.

To get the packages, go to packages.ubuntu.com.  You will need to browse the section of the Ubuntu version you are using (Feisty) to find wifi-radar.  Since you are using feisty, network-manager should be installed somewhere, idk where tho (never used it, wifi-radar has always worked for me).  Select the wifi-radar package and save it to something that you can transfer to the laptop.

Put the package in your /home/<username> folder.  Then right click and select the install option.  I just checked and their shouldn't be any dependency issues, so that should be the only package you need.

Once this is done fire it up (might be a menu item somewhere, otherwise wifi-radar from the terminal) and see if you can connect.

---

### Post by olileauk on 2007-03-28
this laptop is old and has no ethernet port. Thanks for the advice though, i'll do that now.

---

### Post by dstew on 2007-03-28
You could try to configure your wireless using iwconfig. Then you wouldn't have to install any new programs.

EDIT: Is your channel set correctly? Use **iwlist** to see the available settings.

---

### Post by olileauk on 2007-03-28
and how would i go about doing that?

---

### Post by dstew on 2007-03-28
Look at the parameters in your iwconfig output. You can set many of them using iwconfig also (see **man iwconfig**). To list what settings your driver/hardware can manage, use **iwlist**. For example, is your frequency set correctly? Make sure that the frequency you have set matches that of your access point. To change it, use sudo iwconfig wlan0 channel #

---

### Post by olileauk on 2007-03-28
using iwlist, i have [interface] repeated a lot followed by (as they appear) scanning, frequency, channel, bitrate, rate, encryption, key, power, txpower, retry, ap, accesspoints, peers, events.

i have no idea what that tells me.

and the wifi-radar doesn't work, so i'm (slowly) installing network manager.

EDIT: wifi-radar now finally detects leanet but when i connect i get the message "could not get IP address"

which is odd.

---

### Post by olileauk on 2007-03-28
this is very, very confusing.

I installed network-manager so now i can look for networks automatically, however i cannot install the GNOME frontend for it becuase there are 2 files i don't have who will not install unless the other is preinstalled - ergo, endless loop.

---

### Post by olileauk on 2007-03-29
right, well i now have no idea what's going on with this, it seems needlessly complicated, especially when ubuntu feisty just have a network monitor built in to it.

Is there any last suggestion anyone has before i got back to ubuntu?

---

### Post by dstew on 2007-03-29
If you really need xubuntu, you will probably have to keep trying to configure using the command line tools. I should have said iwlist wlan0 before, not just iwlist.

Anyway, I got my card working using the command line tools in xubuntu. But I am not really an expert. I just kept trying different settings using iwconfig wlan0, and eventually it started working. I don't really know why.

There are also configurations for the interface itself, using ifconfig wlan0. There are also ifup and ifdown, to start and stop an interface.

---

### Post by qamelian on 2007-03-29
> **olileauk said:**
> this is very, very confusing.

I installed network-manager so now i can look for networks automatically, however i cannot install the GNOME frontend for it becuase there are 2 files i don't have who will not install unless the other is preinstalled - ergo, endless loop.

If the two files are in the same directory, you can install them both simultaneously to avoid this circular dependency. To install file1.deb and file2.deb at the same time, open a terminal and type:

```
sudo dpkg -i file1.deb file2.deb
```
Both packages will resolve and install so long as their is no third dependency missing.

---

### Post by olileauk on 2007-03-29
meh, this is getting way too complicated for someone who doesn;t know what they're doing in the first place. back to straight ubuntu, methinks.

thanks for the help though eveyone.

---

