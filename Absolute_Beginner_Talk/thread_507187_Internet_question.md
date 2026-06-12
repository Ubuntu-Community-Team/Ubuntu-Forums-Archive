---
title: "Internet question"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by crazydude2007 on 2007-07-22
I just installed Ubuntu. I thought I was going to loose my mind, but it finally worked. I now have another problem, and I am sure it is just something that I do not understand how to do, since I am very new to Linux. I have a Wireless USB adapter connected to the computer, and I was wondering how to set it up in Ubuntu, because as far as I understand it doesn't see my wireless adapter at the moment? Thanks in advance :)

---

### Post by bradleyd on 2007-07-22
what wireless adapter is it. What version that sort of thing.

---

### Post by crazydude2007 on 2007-07-22
> **bradleyd said:**
> what wireless adapter is it. What version that sort of thing.

It is a Linksys Wireless-G USB Adapter. How do I set it up. For example it works in Windows because it sees it and everything, I don't know how to make it work in Ubuntu?

---

### Post by bradleyd on 2007-07-22
what is the model #

---

### Post by crazydude2007 on 2007-07-22
> **bradleyd said:**
> what is the model #

[http://www.superwarehouse.com/p.cfm?p=330247&CMP=KAC-PositionTechFeed](http://www.superwarehouse.com/p.cfm?p=330247&CMP=KAC-PositionTechFeed)

---

### Post by bradleyd on 2007-07-22
you need to use ndiswrapper and the Windows drivers for the adapter. These directions are for 64 bit version but will do fine. [QUOTE] Step 1

So you need to blacklist it first in a file situated in etc/modprobe.d/


Code:
$sudo gedit /etc/modprobe.d/blacklist
add the following line in the blacklist file

blacklist rt2570

save and restart. Check that after restart your wireless rausb0 disappears leaving only the modem in admin -> network.

Step 2
sudo apt-get install ndiswrapper-common ndiswrapper-utils

Now ndiswrapper is installed

step 3

Installing the drivers is next. Pop in your WUSB54G installation cd. And find the drivers. For me it is version 4. So i copied the version 4 directory which is WUSB54Gv4. Copied the folder to my user directory.


Code:
/home/username/WUSB54Gv4
First check any drivers in ndiswrapper.

Code:
$sudo ndiswrapper -l
if there are any drivers installed uninstall it by


Code:
$sudo ndiswrapper -e drivername
follow by installing from the directory the inf file


Code:
$sudo ndiswrapper -i drivername
please remember the inf extension. In my case the drivername is rt2500usb.inf

So now restart and wireless should work. Configure your wireless connection in admin -> network[/QUOTE

---

### Post by delacerda on 2007-07-22
You'll need to install ndiswrapper from the repositories. Use Synaptic to do this. Next, you'll need the drivers in a folder somewhere on your computer (the .sys and .inf files, not a standalone .exe). Lets assume they are on the desktop. Open a terminal and type the following commands:

```

ndiswrapper -i ~/Desktop/[folder]/[driver].inf
ndiswrapper -m
modprobe ndiswraper
```

*substitute [folder] with the folder name and [driver] with the driver name*

You're adapter should now be installed.

---

