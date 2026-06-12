---
title: "Installing driver (rt2400)"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Atasuke on 2005-12-04
hi there, I want to install the rt2400 drivers for my wireless card seeing as it supports the chipset. 

however I am a complete newbie to linux and need help. I don't even know how to install drivers. :( I learn't some basic shell commands but thats about it really.

In in the instructions it says:

run makefile
run make

and thats in the file called INSTALL which i opened using "less INSTALL"

but I don't get it because when I type "make" it says there's no such command.

Please help a complete and utter n00b. I don't want to give up on ubuntu and am determined to get my wireless network going.

If it helps...my wireless card is a Belkin 802.11g Wireless Network Card

Thanks.

---

### Post by Lambert on 2005-12-04
rt2400 is built into breezy. Pop the card in, go to system>admin>networking and try to configure.

To see that the driver loaded type this command at terminal

sudo lshw -C network

look for the line configuration:

you will see something in that line like driver=xxxx

---

### Post by Atasuke on 2005-12-04
Thanks for the info I typed what you said and it listed the driver installed, so I guess that part of it worked.

I went to system > admin > networking and tried to configure

it seems to be picking up the broadcasted ssid but when i click ok it does its activating ra0 stuff then finished and nothing else happens, i'm not sure if it even connects to the network. No flashing lights on my card to indicate network traffic and no web pages actually load. Though it does pick up the SSID so I take it that the driver is functioning somehwhat. Do I need third part applications in order to control my wireless card by any chance?

Sorry to trouble you

---

