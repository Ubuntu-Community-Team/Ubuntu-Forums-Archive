---
title: "R60 Thinkpad and ubuntu"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by oldone on 2006-12-02
I am looking at buying an R60 Thinkpad with Intel Pro wireless card included. Does anyone know if this will work with Ubuntu?

---

### Post by wjp.reg on 2006-12-02
I've been running a Lenovo 3000 N-100 with the intel prowireless 3945ABG with no difficulties and "out of the box" :-)

---

### Post by oldone on 2006-12-02
Ok, thanks!

---

### Post by pionium on 2006-12-03
hi, i have the R60e with Kubuntu. Althou it works, there is an issue with the 3945ABG wireless - I have to toggle disable/enable in Network Settings before the card can connect to the router. I think there is a workaround, but I haven't found it as of yet.

---

### Post by oldone on 2006-12-03
I heard something about this but could you please explain a bit more. If it is a matter of shutting it off and turning back on  then that is not that bad!!! Thank you.

---

### Post by pionium on 2006-12-06
Sorry for the delayed reply.

It seems it was my fault is wasn't working properly; I had the wrong ESSID key .. Other than that all I hear is that it works out of the box with Dapper and Edgy.

---

### Post by oldone on 2006-12-06
Thanks - dumb question, but could you please explain in detail what the isse was and how you fixed it?  Thanks.


also - How do I install the disk from boot or on boot?  I do not use windows, only macs, so I am not sure if I can install from the desktop CD icon in windows which should work??? or install with some command - on macs it is hold down C key on boot and that is it.  people at lenovo refuse to answer this question for multiple reasons.  Also I know nothing about doing it in safe mode or whatever and also how to even get to safe mode or whatever it is called - Bios? or some such thing.

be detailed please.  thank you so much.

---

### Post by pionium on 2006-12-07
I must say I'm still a novice in Linux, but I'll share with you how I managed this (thanks to trubblemaker).

The ESSID key is obtained by scanning for available networks.

To scan for networks, use:
```
sudo iwlist scan
```
My laptop is configured with eth1 designed to the wifi card and the result for this device was:
```
eth1      Scan completed :
          Cell 01 - Address: 00:17:9A:6E:D5:5F
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=77/100  Signal level=-57 dBm  Noise level=-57 dBm
                    Extra: Last beacon: 276ms ago
```
In this case ESSID is "dlink" (see 3rd line). At first I had problems cause by me applying the wrong ESSID to the eth1 entry in /etc/network/interfaces. Edit this file as root to make the the eth1 entry look something like this: 
```
auto eth1
iface eth1 inet dhcp
wireless-essid dlink
```
ps: Note that dlink is not in quotes.

Regarding your other question; if you mean installing Ubuntu, it's very straight forward - just boot from your Ubuntu live CD.

Enter Bios by pushing F1 (or Delete on some systems) on startup. Change boot order to say "boot from CD/DVD drive" as first device. Enter your Ubuntu CD, save/exit bios and your PC restarts automatically. 

The installation process is explained in the install guide:
[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)

ps: Lenovo usually ships laptops with winXP preinstalled and with a rescue partition. This occupies some space, but I'd advice against removing it. After all, you have paid for it. Although I rarely use winXP on my laptop, I had it installed just in case.

I hope this answers your question. Please do ask again if it doesn't.

---

### Post by oldone on 2006-12-07
Ok - Thank you so very much. I do not know command line stuff so I will have to be careful on what I am doing... Also - the boot up also scares me a bit since I know zero of windows.  I guess you cannot load from the lice CD in windows - i.e. click on the CD Icon on the widnows desktop and then go from there.

I hope this works.  I bought this r60 basic model just to run and try to learn Ubuntu linux.  if this does not work, I have a useless computer. I refuse to run windows.  Hence the macs in my house.

thank you again!  I may ask more questions.

anyway we can correspond through email for a few follow up questions in case you do not check back this thread in the future. My laptop should be here next week sometime....

---

