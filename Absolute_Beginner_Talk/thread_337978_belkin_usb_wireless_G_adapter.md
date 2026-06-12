---
title: "belkin usb wireless G adapter"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by spellico on 2007-01-13
I'm trying to iinstall a driver for a Belkin usb wireless G adapter F5D7050 . I have downloaded the driver  zd1211-driver-r83 but I have no clue as to how to install it. I searched the forum and found several posts but none has worked. Of course the reason is that I'm an absolute beginner and I'm trying to learn even the basics. Any help with some simple instructions ?  Thanks so much for your time.

---

### Post by jas0 on 2007-01-13
First of all we need to know what form you have the driver in. Is it a .deb file? tar.gz/bz? Also, have you tried just plugging it in and seeing if it works?

---

### Post by spellico on 2007-01-13
Thanks. It's a tar.gz file. I extracted it to my desktop ... as far as just plugging it , how? where? Thanks again.

---

### Post by jas0 on 2007-01-13
Try just pluggin the adapter into a USB port on your computer and then open a terminal window and type:

```
iwconfig
```

---

### Post by spellico on 2007-01-13
I tried that. It just doesn't see the adapter and it doesn't see any wireless connection.:(

---

### Post by jas0 on 2007-01-13
Well in that case just unarchive your driver, open a terminal window, navigate to the folder where your driver is and type:

```
sudo ./configure
sudo make && make install
```

---

### Post by spellico on 2007-01-13
I feel pretty ignorant ... well I am. Is unarchive the same as extract ? that's what I don't understand. Right now the extracted file is on the desktop. what would I type  Desktop and then sudo ./configure ? Thanks again.

---

### Post by jas0 on 2007-01-13
I'm assuming you have the driver downloaded to the desktop. Here's what you do:

First of all open a terminal window, you'll do everything from there

Now that you have the terminal window open, type the following commands:

```
cd Desktop
ls -al *(to find out the exact name of the driver package)*
tar xzf package.tar.gz
ls -al *(to find out the name of the directory the package was extracted to)*
cd NewPackageDirectoryName
sudo ./configure
sudo make && make install
```

Hope that helps.

---

### Post by spellico on 2007-01-13
I'll try right now. I have to switch from windows because obv I have no connection. Thanks a lot.

---

### Post by spellico on 2007-01-14
Well, I've found out that ubuntu already has a driver for the belking usb it's module rt2570. Trouble is that the Belkin usb is recognized (I ran lsusb ) but there is no driver associated to it (configuration line no driver ). I tried to unplug it and plug it back in . Nothing. Also in Networking there is no "Wireless Connections". How do I associate the driver with the device? Any help? Thanks very much.

---

### Post by chris027 on 2007-09-01
ok, sorry for jump starting an old thread, but this one ain't quite finished and I'm having the EXACT same problem this guy was having back then. 
I went to the hardware profiler, where it is listed as "belkin adapter" in the chain, but everything about it is unknown. The network utility on top of the desktop is finding my linksys network but will not connect to it (i made the network open to simplify things). 
I found the ralink driver (RT73_linux_sta 1.0.4.tar.gz) and pasted it to my desktop, but don't know what to do with it. I can easily find the pages with all the terminal jargon mumbo jumbo, but if i knew what that stuff meant I wouldn't be here on the noob site, so, if anyone could help me get online, I would definitely appreciate it and be in your servitude for eternities to come!
I'm using ubuntu 7.04

---

