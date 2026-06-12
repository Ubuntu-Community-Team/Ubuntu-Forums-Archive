---
title: "[SOLVED] Macbook Pro wireless problem"
date: 2008-12-14
forum: Apple Hardware Users
---

### Post by luke white on 2008-12-14
Hi,

I have installed Ubuntu 8.10 on my macbook Pro (2 Ghz Core Duo). Yesterday, after installing, the wireless was fine - it worked "out of the box" just as the help pages on installing Ubuntu 8.10 on a macbook pro said it would. 

However, today the network manager (in the top right of the screen) does not give me the option of a wireless network. I searched the wireless troubleshooting pages of the Ubuntu documentation and it suggested I run "sudo lshw -C network". This revealed that what I assume is the wireless card seems to be "unclaimed." The output for this is as followed:
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

The documentation then points me to how to use windows drivers for hardware - which seems not to be of use since I'm a mac user.

The only thing that I can think of that might have made the card - which showed up and worked fine yesterday - disappear for linux is having run the system updater. Has anyone else had this problem? Has this messed something up? How can I get the card up and running again? Do I need to re-download drivers?

Thanks in advance for any help!

Luke

---

### Post by bryonak on 2008-12-14
You should always mention which generation of MacbookPro you use, which you
can find out by typing this into a terminal:
```

sudo dmidecode -s system-product-name
```

Wireless has become much simpler with Ubuntu 8.10 on MacbookPro's. For more info, read my comments in [this thread]("http://ubuntuforums.org/showthread.php?t=1004538").

---

### Post by luke white on 2008-12-14
Thanks very much for your help Byronak. I think I have sorted this out now - from the posts on the link you gave, along with the MacBook Pro Community Documentation, and with a bit of the kind of detective work that I am starting to learn is important when you are a Linux user! 

For anyone that is looking through these posts that might have suffered a similar experience, who wants to know what I think the answer is, and/or what I did to get things going :

(1) My Macbook Pro model is 1,1.
(2) I think that what has happened is that the driver which comes with my Ubuntu 8.10
Cd - according to the Community documentation (see [https://help.ubuntu.com/community/MacBookPro#Wireless](https://help.ubuntu.com/community/MacBookPro#Wireless)) madwifi - seems to have recently become obsolete and removed from Ubuntu. Thus I am guessing that when I updated my system using system upddate, it removed it from my computer - hence my inability to see any wifi options in the network manager menu. madwifi was not / no longer listed in the /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless directory. The solution, I decided, was to install the other driver mentioned in the Documentation pages - ath5k.
(3) It says in the Documentation pages that this is in a package called linux-backports-modules-intrepid. In order to install this, I went into System->Administration->Synaptic Package Manager, and in this clicked on search and typed in 'backports'. From the list of packages that came up I selected linux-backports-modules-intrepid, and clicked on the green tick at the top of the window to get it to go ahead and install. (Obviously, to do this I had to plug myself in to an ethernet (wired) network, since the wifi no longer worked!!) When I restarted the computer, the wifi option was once more available in the network manager. And here I am sending this over wifi again!

My guess is that there will be a few people with old Macbooks like me who will be similalrly affected by this phenomenon, and so I hope these instructions will be of use in sorting this out - especially for other "newbies" like me!

Luke

---

### Post by cyberdork33 on 2008-12-15
> **luke white said:**
> Thanks very much for your help Byronak. I think I have sorted this out now - from the posts on the link you gave, along with the MacBook Pro Community Documentation, and with a bit of the kind of detective work that I am starting to learn is important when you are a Linux user! 

For anyone that is looking through these posts that might have suffered a similar experience, who wants to know what I think the answer is, and/or what I did to get things going :

(1) My Macbook Pro model is 1,1.
(2) I think that what has happened is that the driver which comes with my Ubuntu 8.10
Cd - according to the Community documentation (see [https://help.ubuntu.com/community/MacBookPro#Wireless](https://help.ubuntu.com/community/MacBookPro#Wireless)) madwifi - seems to have recently become obsolete and removed from Ubuntu. Thus I am guessing that when I updated my system using system upddate, it removed it from my computer - hence my inability to see any wifi options in the network manager menu. madwifi was not / no longer listed in the /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless directory. The solution, I decided, was to install the other driver mentioned in the Documentation pages - ath5k.
(3) It says in the Documentation pages that this is in a package called linux-backports-modules-intrepid. In order to install this, I went into System->Administration->Synaptic Package Manager, and in this clicked on search and typed in 'backports'. From the list of packages that came up I selected linux-backports-modules-intrepid, and clicked on the green tick at the top of the window to get it to go ahead and install. (Obviously, to do this I had to plug myself in to an ethernet (wired) network, since the wifi no longer worked!!) When I restarted the computer, the wifi option was once more available in the network manager. And here I am sending this over wifi again!

My guess is that there will be a few people with old Macbooks like me who will be similalrly affected by this phenomenon, and so I hope these instructions will be of use in sorting this out - especially for other "newbies" like me!

LukeThanks!

---

