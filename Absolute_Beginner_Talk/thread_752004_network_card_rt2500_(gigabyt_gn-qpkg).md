---
title: "network card rt2500 (gigabyt gn-qpkg)"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by austclint on 2008-04-11
hi

i have just downloaded Ubuntu server 7.10 and i am bran new to linux and i am trying to get my wireless card to work, it is saying i do have a wireless network but it is connecting, some seach trough google i have found i need to update the drivers, and i cant find anywhere the helps me to install them.

if someone could show me where to fined a tutorial on how to install network card drivers thats would be good, i have downloaded the source drive for the rt2500

thanks

---

### Post by mikeyphi on 2008-04-11
> **austclint said:**
> hi

i have just downloaded Ubuntu server 7.10 and i am bran new to linux and i am trying to get my wireless card to work, it is saying i do have a wireless network but it is connecting, some seach trough google i have found i need to update the drivers, and i cant find anywhere the helps me to install them.

if someone could show me where to fined a tutorial on how to install network card drivers thats would be good, i have downloaded the source drive for the rt2500

thanks

Hi there and welcome!
rt2500 is the driver name. Do you have a name for the chipset in your card?
In the past gigabyte cards using the rt2500 driver have worked 'out of the box'

what does your system say about the card if you enter code:
lspci

---

### Post by austclint on 2008-04-11
02:a0 Network controller: RaLink RT2500 802.11g Cardbus/miniPCI (REV 01)

---

### Post by hyper_ch on 2008-04-11
that should be working out of the box....

what do you get by running:

```

iwconfig

```

and

```

ifconfig

```

---

### Post by wieman01 on 2008-04-11
Mine (rt2570) does not work out of the box either. I use 'ndiswrapper' therefore.

---

### Post by aeiah on 2008-04-11
try here:
[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

or do a search for 'rt2500 serialmonkey'. i use the linux serial monkey drivers instead of ndiswrapper (ndiswrapper uses the windows drivers and wraps them up in a package that communicates with linux properly)

---

### Post by mikeyphi on 2008-04-12
Just seen a post from a Hardy user - the rt2500 seems to 'work out of the box'
You might want to try that - Hardy is not quite ready for general release but a look at the latest might be worthwhile!!
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by austclint on 2008-04-16
I have played around and have got it too pickup the mac address of my router (billion BiPAC 7404VGP) but its not getting and signal (Link Quality=0 Signal level=0 Noise level=0) i used this code```
iwconfig wlan0 mode managed essid shale channel 1
```

---

### Post by mikeyphi on 2008-04-19
> **austclint said:**
> I have played around and have got it too pickup the mac address of my router (billion BiPAC 7404VGP) but its not getting and signal (Link Quality=0 Signal level=0 Noise level=0) i used this code```
iwconfig wlan0 mode managed essid shale channel 1
```

OK - have you tried changing the channel number?
I know my router is on channel 6 - If you don't know the correct channel you could try them all until you get a good signal!!

---

### Post by austclint on 2008-04-20
it is channel 1

---

