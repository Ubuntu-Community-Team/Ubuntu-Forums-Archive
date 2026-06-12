---
title: "I need help for a couple of problems"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by mehmet.ali.anil on 2007-06-28
Hi.

I am trying to be an Ubuntu user for four days today and I am struggling with problems which are new to me and probably boring to you.
My problems are already discussed in the forums but I couldn't fix them by the methods that I read, they were too hard or they didn't work out.

I messed up with the OS too much, now it is frozen on startup, but I am going to reinstall it.

One of my problem is with the wireless adapter. I have a USB wireless adapter manufactured by ASUS,   
 WL-167g 
My desktop connects via this device; to my wireless ADSL modem to the internet. The Network Manager is incapable of making the device connect to my wireless network. WEP, WPA, unsecure.. it doesn't matter.

I can see that the Os can recognize my wireless device when I try ```
lsusb
```. It states that it is an ASUS device, but no other information is given. When I plug out the  adapter, it is not recognized till I restart my computer; just as if the adapter is plugged via a COM port.

I tried to install ndiswrapper to reinstall a newer driver, but I couldn't suceed in that. I tried WICD, It supported WPA for the first time but couldn't connect also. The networks are always shown with low signal strengths, though my Windows laptop that I am using now tells that it is 'Good'.

My Nvidia driver is not supported also, but this is a secondary problem.

Thanks a lot.

---

### Post by overdrank on 2007-06-28
> **mehmet.ali.anil said:**
> Hi.

I am trying to be an Ubuntu user for four days today and I am struggling with problems which are new to me and probably boring to you.
My problems are already discussed in the forums but I couldn't fix them by the methods that I read, they were too hard or they didn't work out.

I messed up with the OS too much, now it is frozen on startup, butI am g


Ok

---

### Post by mehmet.ali.anil on 2007-06-28
pardon me. I accidentaly sent the message unfinished.

Last thing I was trying to do was installing ndiswrapper. It freezes on the loading screen right after i type my username and password.
I am probably going to reinstall it, since I cant have a data loss..
But I will face the same problems with my wireless, probably.

---

### Post by mehmet.ali.anil on 2007-06-28
I have found the drivers for he chipset RT2500USB for Linux

But it seems to be a bunch of .c and .h files, can someone help me with installing these drivers?

---

### Post by aeiah on 2007-06-28
ah, worry not. rt2500 drivers are fairly simple to install. what you've got there is the source files. you'll need to compile them, apply the driver module, and insert information into certain files that'll tell your card what to connect to etc.

there should be a tutorial for it on this forum somewhere, although it isnt jumping out at me right now...

---

### Post by aeiah on 2007-06-28
in fact, rt2500 drivers should be installed by default. what does the command iwconfig show?

---

### Post by mehmet.ali.anil on 2007-06-29
The output is:
```

lo        no wireless extensions. 
 
rausb1    RT2500USB WLAN  ESSID:""  Nickname:"" 
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s    
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-217 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Does this mean that rt2500 is already installed?
Than what could be the main problem ?
I reinstalled Ubuntu, and I am trying Wicd now.

---

### Post by hyper_ch on 2007-06-29
You didn't set a ESSID - the name of the network you want to connect to...

---

### Post by mehmet.ali.anil on 2007-06-29
I generally select ESSID from the router list from Wicd or Network Manager,
Should I specify it in a configuration file also?

---

### Post by hyper_ch on 2007-06-29
I dunno what you use... I use the provided network manager by Xfce and I just enter my ESSID in there and that's it...

The network manager does then save the configuration file with the ESSID

---

### Post by mehmet.ali.anil on 2007-06-29
Actually when I use Network Manager or Wicd, The networks around me are recognized. Thier ESSID s and their other specifications that I am unable to name such as Hex codes like 00:14:bf:c6:61 It can also show hat It is a secured network. 

The problem is that when I try to connect with one of these programs, the signal ratio is always low (Wicd shows %-1 ), *though it is not* the usb adapter doesn't even give show pulses via the communication LED.

I am stuck between the drivers or the OS or the hardware while trying the diagnose the problem.

---

