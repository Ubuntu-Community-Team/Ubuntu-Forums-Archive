---
title: "Can Not Connect To Internet"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Sketch on 2006-08-29
In my house there is a Wireless network set up.  A network key is needed to connect to the network.

Yesterday, I reformatted my computer and installed Windows XP and then installed Linux on 2 separate drives

When I booted the computer into Windows, the internet connection was automatically detected, I typed in the network key and was connected to the internet with no problem.

When I boot the computer into Linux and open Firefox, a page is displayed reading Server not found

What steps must be taken to connect to the internet using Linux?

---

### Post by Sketch on 2006-08-29
Does Anyone know where I type in my WEP Key to connect to wireless router?

---

### Post by nickpaton on 2006-08-29
Hi Sketch and welcome to the forums!

So as to help you, we do need more information.

So as to identify the Wireless chip in your PC please would you post the results of the following command:

```
iwconfig
```

(To do this, open a Terminal, which can be found under Applications>Accessories.

At the prompt, simply type in the above command)

---

### Post by Sketch on 2006-08-29
iwconfig

lo    no wireless extensions

eth1  no wireless extensions

eth0  no wireless extensions

wlan0 no wireless extensions

sit0  no wireless extensions

---

### Post by nickpaton on 2006-08-29
Mmmm it's saying that you do not have any wireless device at all.

Can you go into System>Administration>Device Manager and see if there is a wireless device listed.

Are you sure that you have your wireless switched on?

---

### Post by Sketch on 2006-08-29
I Have 2 Ethernet connections

eth1

eth2

I have a usb connection plugged in, the usb is connected to a reciever of the wireless router

---

### Post by Sketch on 2006-08-29
if you were going to ask

ifconfig

eth0       Link encap:Ethernet   HWaddr  00:04:75:AB:00:FD
           UP BROADCAST MULTICAST   MTU:1500   Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
           Interupt: 193

lo         Link encap: Local Loopback
           inet addr: 127.0.0.1   Mask:255.0.0.0
           inet6 addr:  ::1/128 Scop:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:277 errors:0 dropped:0 overruns:0 frame:0
           TX packets:277 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:21240 (20.7 KiB)   TX bytes:21240 (20.7 KiB)

---

### Post by nickpaton on 2006-08-29
Can you tell me the make/model of your PC or laptop, and whether it has a wireless card fitted in a slot or as part of the machine itself.

---

### Post by Sketch on 2006-08-29
I am using a PC, not a laptop

AMD Athlon XP, 1800 MHz

---

### Post by Sketch on 2006-08-29
I have a USB cable plugged into the back of the computer.
The cable of the usb cord connects to a receiver
The receiver is wirelessly connected to a wireless router on the other side of the house
The router is connected to a cable connection

---

### Post by nickpaton on 2006-08-29
Thanks for that Sketch.

You're getting outside of my experience.

I've done a quick Search for 'USB Wireless' on the forums and come up with a lod of results.

May I suggest you go through them to see if any fit the bill?

Also to help someone else with more knowledge, please can you post the make/model of your wireless USB device.

Can someone else help with a USB connection to a wireless router?

Sorry M8 - I'll keep an eye though and good luck!

---

### Post by Sketch on 2006-08-29
I am not sure, but I think I am using

some of this print out where i am getting the information was cut off toward the right side, hope this is correct



Network Adapter     3com EtherLink XL 10/100 PCI
Network Adapter     Microsoft Broadband Networking
Network Adapter     Realtek RTL8029 (AS)-based ET
Modem               Generic Soft56K

---

### Post by nickpaton on 2006-08-29
Sorry Sketch my fault - what is the make / model of the USB wireless receiver.

Actually it may be the Realtek, but would be grateful if you can confirm.

I'm asking this so that someone more knowledgeable than me can help you.

Sorry for all the questions!!

---

### Post by Sketch on 2006-08-29
On the back of the Receiver is written

Microsoft Broadband Networking Wireless USB Adapter

Model: MN-510

---

### Post by nickpaton on 2006-08-29
Sketch - give this a few hours.

If no one posts can I suggest a new one with all the details you've given?

---

### Post by Sketch on 2006-08-29
Thank You Nick, For your help

I hope someone replies with a solution

---

### Post by nickpaton on 2006-08-29
Sketch

Just dug this out from a forum search:

[http://http://www.linuxquestions.org/hcl/sh...cat=146&page=1]("http://http://www.linuxquestions.org/hcl/sh...cat=146&page=1")

Try putting mn-510 into the search under advanced  & titles only.  There are some posts which are somewhat old but may give a clue.

Anyone else help here??

---

### Post by Sketch on 2006-08-30
DAY 2
__________

I installed linux-wlan-ng from the Synaptic Package Manager

After Restarting the computer, Administration -> Networking now recognizes that there is a Wireless connection named wlan0

The Internet Still does not work and I am prompted with a server not found screen

I tried Deactivating and Reactivating Wireless connection, but the internet still does not work

I just installed ndiswrapper, although I am unsure of how to use this tool.

Please Help!

---

### Post by Sketch on 2006-08-30
In terminal when I type

iwconfig there is now showing

__________________________________________________
wlan0      

IEEE 802.11-DS   ESSID:"dj"   Nickname:"dj"
Mode:Ad-Hoc   Frequency:2.412 Ghz   Cell: 02:50:c3:28:41:32
Bit Rate:1 Mb/s   Tx-Power:18dBm
Retry min limit:8   RTS thr:off   Fragment   thr:off
Link Quality=0/92   Signal level=-100 dBm  Noise level=-100 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0   Invalid misc:0   Missed beacon:0
__________________________________________________

--Still no internet connection--

---

### Post by nickpaton on 2006-08-30
Sketch - can I suggest posting this in the Wireless section, with a reference back to this post.
Supply all the relevant info that's here so that people aren't asking the same questions again.
There will be someone who can walk you through this, don't worry.

---

