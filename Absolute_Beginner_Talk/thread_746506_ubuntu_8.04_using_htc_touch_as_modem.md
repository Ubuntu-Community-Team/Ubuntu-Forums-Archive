---
title: "ubuntu 8.04 using htc touch as modem"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by ndreamstate2 on 2008-04-05
hello everyone. I have an HTC touch from alltel and i use it to get on the internet with my laptop. I live so far out that its the only source of internet for me. i just got the new ubunu 8.04 and would like to know if and how i can use my htc as the modem

---

### Post by estaticd on 2008-04-14
This might help you... thread is a long read, might want to start from the beginning.

[http://ubuntuforums.org/showthread.php?t=343989&page=11](http://ubuntuforums.org/showthread.php?t=343989&page=11)
post# 108

---

### Post by trondhuso on 2008-04-16
When I plug in the mobile phone into the USB-port I get these messages:
Apr 16 19:49:07 ubuntu kernel: [  584.140000] usb 4-1: new full speed USB device using uhci_hcd and address 3
Apr 16 19:49:07 ubuntu kernel: [  584.308000] usb 4-1: configuration #1 chosen from 1 choice
Apr 16 19:49:07 ubuntu kernel: [  584.396000] eth2: register 'rndis_host' at usb-0000:00:1d.3-1, RNDIS device, 80:00:60:0f:e8:00

Then after some time, the time it takes for the phone to turn off the lights, I get this message:
Apr 16 19:51:09 ubuntu kernel: [  705.892000] eth2: unregister 'rndis_host' usb-0000:00:1d.3-1, RNDIS device

I'm running Ubuntu Gutsy 7.10, but I am planning on upgrading to 8.04.

The USB also comes up as a wired network (unknown USB interface)

Any tips on how to use this as a modem. I would very much like to help out to get HTC phones to work as a modem under Linux.

-----

Just want to mention that by following the howto in the PDF that follows the link above, I have now connected my HTC Touch Duo with Ubuntu Gutsy and is now surfing the web through my mobile. Now I want to help out creating an application that will help connecting to your phone through BlueTooth and such. If anyone know anyone who wants to take part, please do let me know.

Update 2:
I have created the following script thanks to the post above. I run this every time I want to connect to the internet using my phone (and I am doing that quite a lot on the train for instance)

#!/bin/bash

# make sure that the hci_usb is in the kernel module.
sudo modprobe hci_usb reset=1

# Connect to the phone
sudo pand --connect <YOUR PHONES MAC ADDRESS> -n

# Then connect to network
sudo ifup bnep0

Under Hardy I have to set DHCP on the bnep0 under Network when it comes up. Without it you don't get any IP-address. 
Good luck to those using this small script.

---

