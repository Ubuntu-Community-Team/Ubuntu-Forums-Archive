---
title: "[SOLVED] Beginning to prepare for Arch... How do I find Network info. in Windows Vist"
date: 2008-12-22
forum: Arch and derivatives
---

### Post by Redrazor39 on 2008-12-22
I plan to dual boot Windows Vista Business and Arch Linux (used to be Ubuntu), and I wanted to use the FTP install because I have a pretty good internet connection. The installation guide I printed off directly from archlinux.org is telling me I need this network information to connect to the internet:

[B]IP Address

Subnet Mask

Gateway

Ethernet Module for your network card (eg.: eepro100, 8139too, ne2k-pci, etc.)[/B]   

Where can I get this information? I'm on Vista right now.

It's a wireless connection btw.

---

### Post by Redrazor39 on 2008-12-22
Ok I found some of the information by typing in a 192. etc. address into the address bar for my router settings.

Is the IP address the 192.xxx.x.xxx thing I typed into my address bar? Or is it the public IP address that's like 69.etc.?

Lastly, nothing about Ethernet Modules is here, so it must be a hardware thing for my laptop. Do I even need this if I use wireless internet? Where can I find this information if I do?

---

### Post by kk0sse54 on 2008-12-22
You can also open up the command line (cmd.exe) and type ipconfig
which would show you stuff like IP Address, Subnet Mask, Default Gateway, and Connection specific DNS Suffix

---

### Post by Redrazor39 on 2008-12-22
Thanks! Do I need the Ethernet Module if my connection is going to be wireless (probably a stupid question, but I want to make sure)?

---

### Post by COLiNx86 on 2008-12-22
DHCP? that worked for me. you should try just plugging in the Ethernet cable to your laptop and running the network setup thing it's like step 0 in the installer if you choose to do a ftp install.

---

### Post by Redrazor39 on 2008-12-22
lol I don't even have an ethernet cable. I keep my laptop in a room w/out that, so I just use wireless. 

I have IPv4 address, Subnet Mask, and Gateway. I think that's all I need to get on with Arch FTP install, but I just want to make sure so I don't screw up and have to restart everything.

---

### Post by hrod beraht on 2008-12-22
> **Redrazor39 said:**
> Is the IP address the 192.xxx.x.xxx thing I typed into my address bar? Or is it the public IP address that's like 69.etc.?

The reason you need the network information is because during Arch install you have to edit the networking section of the rc.conf (main configuration file in Arch).
The 192.xxx.xxx.xxx address is the address of your computer on the LAN side of your router. The 69.xxx.xxx.xxx address is the address of the actual router on the internet side.
When you set up Arch, your networking section will look something like below, with the bold things being what you have to customize:
```

# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
# HOSTNAME: Hostname of machine. Should also be put in /etc/hosts
#
**HOSTNAME="MyComputerName"**

# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
# 
# DHCP:     Set your interface to "dhcp" (eth0="dhcp")
# Wireless: See network profiles below
#
[B]eth0="eth0 192.168.1.140 netmask 255.255.255.0 broadcast 192.168.1.255"
INTERFACES=(eth0)[/B]

# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
**gateway="default gw 192.168.1.1"**
ROUTES=(gateway)

```

Note: the **etho** (ethernet) part that shows the particular address of **192.168.1.140** is for assigning a static IP address. If you just want to use dhcp and get a randomly assigned address at every boot, you can just use **dhcp** rather than the actual address.

It's actually pretty straightforward. Just follow the [[COLOR="Blue"]Arch Beginner's Guide[/COLOR]]("http://wiki.archlinux.org/index.php/Beginners_Guide") and you can't go far wrong.

Bob

P.S. I'm an Arch/Openbox convert who also came over from Ubuntu, and I couldn't be happier. Welcome aboard. :)

---

### Post by Xiong Chiamiov on 2008-12-22
> **Redrazor39 said:**
> lol I don't even have an ethernet cable. I keep my laptop in a room w/out that, so I just use wireless. 

I have IPv4 address, Subnet Mask, and Gateway. I think that's all I need to get on with Arch FTP install, but I just want to make sure so I don't screw up and have to restart everything.
Getting the network going is one of the very first things you do, so if you can't get it, you've only lost the time it takes to boot up the cd.  You might want to make sure that you install the wireless drivers for your card, though, if they aren't by default.  There are a few things that are on the live cd installation that aren't installed by default (like all the different wireless drivers).

Follow the Beginner's Guide, and you'll be fine.

---

### Post by Nepherte on 2008-12-22
If you are behind a router, use dhcp.

---

### Post by crimesaucer on 2008-12-22
In Vista the terminal the command to check your gateway,subnet,ip address is: 

```
ipconfig
```

For your wireless driver you should check out the name in the drivers section in the Vista drivers section..... I can't remember the exact name of the area but there is a driver area in the system maintenance section somewhere.... Find out the exact name of your card, and then check the Linux forums fro info on it and the correct module name that you might have to modprobe...... with the Arch FTP install, you hopefully will have your wireless detected and installed automatically.

---

### Post by crimesaucer on 2008-12-22
> **Nepherte said:**
> If you are behind a router, use dhcp.

Yes, I 2nd that. DHCP is easy to use. The FTP will automatically configure everything using DHCP.

---

### Post by Redrazor39 on 2008-12-22
Woot alright I've successfully intalled arch and will get to setting up the graphical part later. Now I know how to get connected to my wireless network; something like iwconfig essid (essid) key (key). Anyway, how do I make it so this happens (connecting to my wireless metwork) every time I boot into arch?

---

### Post by crimesaucer on 2008-12-23
> **Redrazor39 said:**
> Woot alright I've successfully intalled arch and will get to setting up the graphical part later. Now I know how to get connected to my wireless network; something like iwconfig essid (essid) key (key). Anyway, how do I make it so this happens (connecting to my wireless metwork) every time I boot into arch?

You would have to have some sort of network profile. Read this section of your /etc/rc.conf and then add the appropriate packages:

```

# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network.d
#
# This now requires the netcfg package
#
#NETWORKS=(main)


```

So check out this wiki page: [http://wiki.archlinux.org/index.php/Netcfg](http://wiki.archlinux.org/index.php/Netcfg)

---

