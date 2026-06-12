---
title: "Can't configure wireless to my Home network"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by jej1216 on 2007-05-10
I just installed Ubuntu 7.04 on my Dell Inspiron.  So far it's great, but I'm having trouble setting up my wireless card.  The card is recognized, but I'm not able to get all of the properties set so it successfully connects.

I have my SSID, and I know the WEP key (64 bit hex).  With my windows PC, I can connect to the WAP and see other settings.  What exactly do I need to connect?  I'm assuming that the drivers must be OK since the card is recognized and I have the option of setting up a wireless connection. 

I've read through the documentation, but I need the instructions watered down even more.

Thanks in advance,

jej1216

---

### Post by annda on 2007-05-10
in order to see if the wifi card is working, you will have to type some things in the terminal.

first find out how the card is called on your system:

```
iwconfig
```

it should be eth1, wlan0 or ath0. when you find that out, see if you have any connectivity.

```
iwlist eth1 scan
```

can it see any networks?

---

### Post by ncasca on 2007-05-10
i am having the same problem as jej... i followed your instructions and it prompted "No scan results"

the iwconfig command shows the following:
```
eth2        IEEE 802.11b/g ESSID:"Linksys" Nickname:"Broadcom 4306"
            Mode: Managed        Access Point: Invalid
            RTS thr:off          Fragment thr:off
            Link Quality: 0      Signal level: 0        Noise level: 0
```

In the network settings menu there is a wireless connection where i can enter in the ESSID, password, static ip settings, but i can't figure out how to establish a connection.... i would sure appreciate any help, still quite new to linux...

---

### Post by annda on 2007-05-10
sorry, but Broadcom is known not to be linux-friendly. unless you can get a "better" card easily and for little money, you will have to work a bit:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

an older thread about ndiswrapper for broadcom:
[http://ubuntuforums.org/showthread.php?t=291088](http://ubuntuforums.org/showthread.php?t=291088)

---

### Post by yaidiot! on 2007-05-10
@jej,

Is the network-manager applet is not working for you? (It should allow you just fill in the blanks for a WEP connection and that card.)

Run nm-applet if you don't already have it in your system tray.

---

### Post by ncasca on 2007-05-11
annda-

Thank you for your response. I guess I am a little confused - I have an HP Desktop that I personally installed the Linksys WMP54GS wireless card for... does this mean that linux is actually not recognizing the card? or is there some relationship involving broadcom and Linksys that i wasn't able to find? Sorry i just can't see what i am missing...

if it is correct, and this is a broadcom/linksys wireless card, then i appreciate your links they look to be helpful if needed...

---

