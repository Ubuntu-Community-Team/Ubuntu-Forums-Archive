---
title: "Centrino monitor mode?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Mr Winters on 2008-03-19
Hey all, about to take the plunge and try to use the ipw2200 driver by following the rather complicated(to me anyway) instructions provided by sourceforge,
I am doing this to enable monitor mode on my centrino mobile technology enabled HP laptop.

Just wondering are there any easier alternatives?

---

### Post by annda on 2008-03-19
hi!

the driver is actually included in ubuntu, it should work out of the box.

if you still cannot configure and use wireless after disabling Ethernet (do this in the terminal):

```
sudo ifdown eth0
```

and (if that didn't work) disabling encryption, please post the outputs of the 'lspci' and 'dmesg | grep ipw' commands. 

and what exactly  do you mean by "monitor mode"?

---

### Post by Mr Winters on 2008-03-20
Thanks!
Well,as much as i can gather, monitor mode on a wireless card is when the card can be used to capture packets in general and is not confined to the wifi network you are connected to. This is used to crack wep keys usually, now of course I'm not doing this illegally as I'm using a personal router as a test subject, just trying to further my knowledge in this department.

Sometimes you can enable monitor mode on your card via the terminal command 
~$ iwconfig eth0 mode monitor, yet unfortunately my centrino card cannot do this and does not seem to have an equivalent mode.

So through installing the driver it changes things so as to enable this mode on the card, and so I was just wondering if there was an easier of doing so.

---

### Post by Mr Winters on 2008-03-20
Ah hah. i've found an easier alternative using a program called aircrack, turns out a command included in this program does it for me, if you're interested here is the thread I found it in [http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276).

---

### Post by Junglizer on 2008-03-20
> **annda said:**
> hi!

the driver is actually included in ubuntu, it should work out of the box.

if you still cannot configure and use wireless after disabling Ethernet (do this in the terminal):

```
sudo ifdown eth0
```

and (if that didn't work) disabling encryption, please post the outputs of the 'lspci' and 'dmesg | grep ipw' commands. 

and what exactly  do you mean by "monitor mode"?

Radio Frequency Monitor Mode or simply 'RFMon' for short. This is often also referred to as "promiscuous mode" that being said, the best way to explain (in my opinion) is to point out that FCC sticker you've probably seen before that reads something like "This device will accept all interference it receives." So what RFMon mode does is allow it to passively use the radio to collect all data on all channels within its range. You'll tend to pick up more networks this way though they may be far enough out of range that you cannot actually connect to them by meeting a minimum data transfer rate. (802.11b has 1, 2, 5.5 and 11 mbps transfer rates) This is b/c RF waves theoretically travel on infinitely however over distance the signal degrades and eventually becomes undetectable by receiving antennas/clients. This is used for WEP cracking b/c you are able to pick up raw data packets that are being passed through the air by network devices within your cards range, and then with the addition of tools like the Aircrack-NG suite, you can crack the encryption using the packets you collect. I will add that it takes a good few hundred thousand unique IV's (packets containing WEP key information) in order to crack WEP. While people go on and on about its insecurities, you may be fine using WEP if you are located in a rural area or have legacy devices that do not support WPA or newer encryptions. Like all security (tech related or not) it is simply a way to increase the time it takes to break in. Nothing is ever 100% secure. 

I hope I didn't bore you guys too much with my explanation. :)

---

