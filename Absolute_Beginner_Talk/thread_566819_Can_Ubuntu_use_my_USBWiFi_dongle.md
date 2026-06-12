---
title: "Can Ubuntu use my USB/WiFi dongle?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by svriderpokey on 2007-10-03
I've tried to use ndiswrapper with the windows driver, but it didn't work.  its a "Dell TrueMobile 1180 wireless USB adapter for Desktops" (which is BS because it has a 6 foot wire on it, but that's beside the point).  I have three guesses, but I don't want to make it worse.  I already don't know how to un-installndiswrapper if it's wrong.

1.  Ndiswrapper is not for dongles, just cards.

2.  I have too many .ini files.
In the ndiswrapper instructions it says to copy the .inf and .ini (if available) files to an ubuntu folder.  My driver CD has two .ini files in the same folder.  I coppied them both.  their names are delsub_5.ini  and delsub_51.ini.  

3.  I used the wrong version of windows drivers for ndiswrapper.
I used the .ini and .inf files that were in the XP folder of the install CD.  Should I have used drivers for a diferent version of Windows?

---

### Post by bsharp on 2007-10-03
I've never used a USB card, but did you install the drivers with ndiswrapper? If not, navigate to the folder in a Terminal and type:
```
sudo ndiswrapper -i driverfile.inf
```
If I remember the instructions correctly, then you type:
```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by svriderpokey on 2007-10-03
I think I did that.  It was a few days ago.  I followed the instructions in the support page.  I can even get so far as to put in my wep/wpa code, it just doesn't find the network.  I'm stuck using XP until I can Get WiFi access to work w/ Ubuntu.

---

### Post by svriderpokey on 2007-10-04
bump.  Sorry, bad form, I know, but I was back to page 5.

---

### Post by ayenack on 2007-10-04
Hello svriderpokey.

Can you  post the output from these commands in a attachment (top of the Message box Attachments little papper clip icon). In Terminal type these one at a time.

[B]lsusb -v

iwconfig

iwconfig -v

ifconfig

sudo lshw[/B]

There'll be quite a bit of output from these.

ayenack.

---

### Post by mybunche on 2007-10-04
I you don't have a solution to your dongle but....
if you need wifi and your current wifi dongle don't work, maybe you could get a Netgear WG111v2. It works out-of-the-box with Ubuntu, don't need to install anything. I use it on my desktop, no problems.

---

### Post by svriderpokey on 2007-10-31
I'm sorry it took so long to properly reply with this.  I don't get much time in front of my computer.  Since posting this I thought it might be easier to try upgrading from fiesty to gutsy first.  I had to zip the .ODT because the file is 20.8 kb and the max for the filetype is 19.5.  Sorry about that, but I can't think of any other way arround it.

This is a dual boot computer.  It is a fresh Gutsy install on a 28 GB partition.  (Guided install on largest free space) I have modified the grub loader to boot XP after 3 seconds (until I can connect to the internet with Ubuntu).  The OS is otherwise bone stock.  

The WiFi adapter is as follows
Dell TrueMobile 1180 wireless USB adapter.  
Model: WL-683D  
IC: 3069B-WL683D
REV A02

---

### Post by ayenack on 2007-11-12
If this card is on Ubuntu 7.10 (Gusty) then it should work out of the box. Do you know how to set the card up to connect to your network, i.e. Systems>Administration>Network your network name etc or by editing network interfaces?

If not post back and we'll try to sort the setup out. You don't need ndiswrapper with this card BTW.

It's a prism2 as listed at the very end of the file you posted. Strange thing is that I can't find it listed anywhere else (should be listed in usb part as well). Only had a quick look at the file you posted so will have proper look to see if it is listed any other place.

[B]*-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: wlan0 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=p80211_**prism2**_usb driverversion=0.2.8 link=no multicast=yes [/B]

ayenack.

---

### Post by diphe on 2008-01-02
Hi, I've the same problem, have you got any suggestion?
I'm using ubuntu 7.04

I've attached the result of the commands you suggested to svriderpokey.

Thank you in advance for the help.

---

### Post by diphe on 2008-01-03
nobody can help me?

thanks in advance

---

