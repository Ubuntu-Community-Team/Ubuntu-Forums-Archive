---
title: "Belkin not Working : F5D7050"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-09-30
Okay from what I hace looked up, I have a V2 or something.

I have done the whole NDIS wrapper and all, and it shows the drivers, however the window shows a message of no hardware for the driver.

What do I do because I love Ubuntu, but am having so many problems with my Dells in loading and settings.

---

### Post by madmatrixz3000 on 2007-09-30
Can anyone help I've looked all over the place and can't find the answers

---

### Post by madmatrixz3000 on 2007-10-07
Please some one help me with ndis Wrapper.  I am completely lost

---

### Post by skymera on 2007-10-07
i have the f5d7000

all i had to do was in

network-admin

change the wireless conncetion to DHCP and then tick the box.
it should reconfigure, if not

sudo /etc/init.d/networking restart

---

### Post by madmatrixz3000 on 2007-10-07
right now it shows the networks, but no signal strength and it will not sink so I'll try that, were you having the same problem

---

### Post by skymera on 2007-10-07
make sure Wired is off (roaming) unticked etc.

no signal? are you in range?

---

### Post by madmatrixz3000 on 2007-10-07
i am next to the router , in windows I get 80 to 90%

And what do I do to roaming?

---

### Post by skymera on 2007-10-07
jus tick the roaming box in Wired connection.

is this a pci card yeah?

ok type 

ifconfig

what is your wireless device called?

---

### Post by madmatrixz3000 on 2007-10-07
this is a usb device on my desktop.

I now see a signal and am connected, I am not able to access the web though

---

### Post by skymera on 2007-10-07
o USB, they buggers they are!

im PCI, try nDisweapper for the .inf file.

i have to go dude, hope all goes well!

---

### Post by skymera on 2007-10-08
so have you any more luck on your Belkin?

try

sudo ifconfig (device name) up

(device name) = replace with name of wireless conenction.

if you dont know try

ifconfig

---

### Post by madmatrixz3000 on 2007-10-09
Ok I loaded the drivers per what the Ubuntu wiki said and now I get nothing.  What do I do?  I really don't have the money to get a new wireless.  And this is a pretty good adapter.

I have an old LINKSYS WUSB54GS USB but I don't know if it still works, or if Linux regonizes it.

Unfortunately, this wirless is really the only thing holding me back, as I cannot download the other essentials I need: Ubuntu Studio, Compiz Fusion, Intel Vid card drivers, VLC.

PS: does anyone know if any of thes common Ubuntu problems, other than Compiz, are solved in the Gusty release.  I have heard rumors about better vid card support is that true?

---

### Post by madmatrixz3000 on 2007-10-09
A ha, gusty does solve the issue with xorg

---

### Post by madmatrixz3000 on 2007-10-10
well so I thought.  I've got the beta and my belkin is having the same problem.

I can see the network, but it will not let me on (there is no firewall or anything just an open router). Please help

---

### Post by olbill on 2007-10-16
I have finally got my Belkin f5d7050 working in feisty and gutsy.   The problem is caused by my version 2.00 being recognized as a version 1.00 by ubuntu.   You can check this by entering the command lsusb in a terminal window.  Ubuntu automaticaly loads the default driver rt73usb for a version 1.00 Belkin 7050.   However the version 2.00 Belkin 7050 requires the rt2500usb driver.  I do not know how to force Ubuntu to use the "wrong" driver without ndiswrapper.   I downloaded the Belkin f5d7050 version 2.00 driver rt2500usb from the Belkin web site.  I then used ndiswrapper to force the system to use the rt2500usb driver.   This has worked great for me.  I hope you have as much luck as I did.  I am using the wireless to send this message.

---

