---
title: "New user trouble with wifi"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by DrPppr242 on 2007-02-23
I'm completely new to linux and installed ubuntu last night on a dell inspiron B130 laptop.  The hardware manager says it has a Dell Wireless 1470 DualBand WLAN and networking recognizes a wireless connection but can't connect to any networks.  I know the network is working properly, but when I scanned with the iwlist command nothing was found, I thought I might need to update drivers, but I can't figure out how to install packages off of my flash drive and can't get them over the internet until I get wifi working, any help would be greatly appreciciated.

---

### Post by annda on 2007-02-23
> **DrPppr242 said:**
> networking recognizes a wireless connection but can't connect to any networks.

what do you mean networking recognizes a wireless connection? how did you figure that out?

---

### Post by DrPppr242 on 2007-02-23
sorry that wasn't very clear I meant went I went system>administration>networking under connections wireless connection was available, as was wired connection and modem connection.

---

### Post by Bachstelze on 2007-02-23
Open a terminal and run *sudo iwconfig*. If your wireless adapter is properly detected, you should have something like that :

```
lo        no wireless extensions.

eth1      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

eth2      IEEE 802.11g  ESSID:"Wifirst-BouguenB-10"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:03:52:D6:48:20
          Bit Rate:48 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=54/100  Signal level=-77 dBm  Noise level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:286071   Missed beacon:0
```

Your wireless interface - eth2 for me but for you it can be something else - is the one that doesn't say "No wireless extensions".

---

### Post by annda on 2007-02-23
this only shows your computer's capabilities. you probably do need a driver. when you figure out which one in right for your wireless adapter, you can download packages from packages.ubuntu.com on another computer or OS, save to you flash drive and get back to ubuntu to install the .deb packages by double-clicking them.

---

### Post by DrPppr242 on 2007-02-23
paul@paul-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

that's what iwconfig showed does that mean that the drivers are ok?

---

### Post by Bachstelze on 2007-02-23
Maybe. Try this

```
sudo iwconfig eth1 essid YOUR_ESSID
```

---

### Post by annda on 2007-02-23
have you tried to configure you wireless before? it seems to want to use an access point with hidden ESSID that is not properly configured - at least that's what i can make of it.

i suppose you have a working driver but the configuration is wrong. can somebody confirm that or am i completely wrong?

---

### Post by Bachstelze on 2007-02-23
It's a bit more complicated than than given that his adapter is a Broadcom. There is a driver for such cars in Ubuntu - that's what he's using now - but it doen't always work. He might have to disable the built-in driver and use ndiswrapper.

---

### Post by DrPppr242 on 2007-02-23
Got it to work after hardwiring it to get online, it turns out that there are drivers in ubuntu without the firmware for legal reasons so I followed a guide off google on extracting the firmware from the windows driver, thanks for the help, also I'm not sure if this is the right place to ask but do you know of a good resource for looking up what terminal commands are and how to use them, I don't understand these sudo commands and such, thanks again.

---

### Post by Bachstelze on 2007-02-23
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)

---

