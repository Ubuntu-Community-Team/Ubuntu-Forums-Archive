---
title: "dell mini card not picking up wireless networks"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by josh air balloon on 2007-10-30
Ubuntu isnt picking up and wireless networks at all.  I know there I get my neighbors signal (its password protected, but Im just trying to see if I can even get it to show up on my computer, and give me the option to log in) but is not.  I had this same problem at school yesterday as well.  Below is what I have: 

Dell Wireless 1390 WLAN Mini Card Rev 3.6 

I dont know if any other information is needed, but I would love it if someone could help me out, please.

---

### Post by amtnbiker16 on 2007-10-30
go to restricted drivers manager and you should see your wireless card driver
if clicking the checkbox doesnt install it (probably not since it should have intalled automatically with the system install), then go to software sources and make sure that the proprietary drivers box is checked
restricted drivers and software sources are both under system administration

of course you need a wired internet connection at this point
anyway, go back to your restricted drivers and enable it again
it should download the drivers and you will be able to see networks

oh yeah, all this works with 7.10, i havent done it on 7.04
you might consider upgrading to it.  it works a lot better for me

---

### Post by josh air balloon on 2007-10-30
Im less than 24 hours new to linux, so I dont know how to get to the "restricted drivers manager"

Everything else Im sure I could figure out, and I might upgrade to 7.10

---

### Post by rbc on 2007-10-30
System--->Administration--->Restricted Drivers Manager. You will have to enter your normal logon password

---

### Post by amtnbiker16 on 2007-10-30
software sources is under the same menu too
click the system menu in the top left corner of the screen, then go down to administration

---

### Post by josh air balloon on 2007-10-30
I updated to 7.10.  I also did the restricted drivers manager thing, it found my wireless card, and updated the drivers.  But its still not picking up any wireless networks.

Maybe Im not looking in the right spot for the networks?  I know on vista, i would go into the network manager and scan for available networks.  Is there an option like this on ubuntu I am not seeing?

As always, thank you in advance for the help.

---

### Post by amtnbiker16 on 2007-10-30
well first be sure there is a signal to begin with

your wireless signals can be found in the top right hand corner of the screen
if youre not connected to any network the icon looks like two computers with an x through them.  

when you click it it is a drop down menu of sorts, any wired or wireless networks show up there.

again, be sure there is a network to see

now did the restricted drivers manager actually download anything or did it just say the driver was enabled because it should have to download something?

good luck

---

### Post by kevdog on 2007-10-30
Go to the command line

To search for wireless network
iwlist scan

If you pick up no networks (and your certain you should have some), please post
lshw -C network

---

### Post by josh air balloon on 2007-10-31
The "command line" is the terminal correct??

I went into the terminal and put iwlist scan and this is what I got:
"lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results"

then i put in lshw -C network and got: 
"WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:4c:37:8c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c8:b8:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.101 latency=64 module=b44 multicast=yes"

Obviously without the quotes ("").  Can anyone translate this?

---

### Post by kevdog on 2007-10-31
Just a question I dont know the answer to

Did the bcm43xx drivers work with this card previously??  Did you install the user space utilites for the bcm43xx driver -- it would have required you to download some additional packages from the internet.

---

### Post by ~chinook~ on 2007-10-31
My performance with this card has been shoddy at best. It routinely doesn't work unless signal strength is in the 70's plus. Kind of frustrating considering it worked fine on windows.

---

### Post by josh air balloon on 2007-10-31
Are you asking basically if the wireless card worked before on windows??  I have no clue if the bcm43xx drivers worked before, how would I know??

"Did you install the user space utilites for the bcm43xx driver"
Where would I find this?  Package manager?  Restricted drivers manager?

---

### Post by kevdog on 2007-10-31
I thought you said you updated??  I guess I might have ascertained incorrectly that you had the wireless drivers working in 7.04.  Sorry about that.

Within Synaptic do a search for linux-restricted.  I should bring up a list of packages.  You need to select the one that matches your kernel -- your kernel version can be found by typing uname -r at the command line.

---

### Post by josh air balloon on 2007-10-31
I did upgrade to 7.10

I went into the terminal and typed 2.6.22-14-generic

In the package manager nothing under 2.6.22-14-generic came up

The closest thing was "2.6.22.14.21 generic linux restricted module"
so I installed that. Is there anything else I need to do?

---

