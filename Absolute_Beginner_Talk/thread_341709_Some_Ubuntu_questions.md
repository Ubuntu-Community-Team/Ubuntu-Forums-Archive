---
title: "Some Ubuntu questions"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by movietrailer on 2007-01-19
Hey, I just put a dual boot of XP and Ubuntu on my laptop, and I'm just kinda exploring everything now.

I have a couple questions about stuff, need some answers:-D 

1. I can't seem to connect to the internet wirelessly, I am now connecting with a 2wire gateway modem plugged into my laptop, and when I connect wirelessly in XP, it works. There is a button I press on my laptop to activate my wireless card when using windows, wondering if that will effect anything on ubuntu.

2. Is there a way to change where I placed ubuntu now? I chose the first "partition drive and use freed space" option but it's not alot of space on the drive, and I have another drive where there's alot of space. I would have put it there, but wasn't given the option.

3. Is there a list of programs that are or are not compatible with Ubuntu?

I'm pretty much an all out newb, so please try to dumb down the responses for right now lol.
Thanks.

---

### Post by mikewhatever on 2007-01-19
Before answering all your questions one by one, you might like to have this guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy).

1. Your wireless connection may need some 'tweaking', so provide more info. It has to be on in the first place, so turn it on with the button.

2. If you are new to Ubuntu, and only just install, your best short would be to reinstall to a more convenient location. If yousing LiveCD, you can choose where to at step 5 of 6 in this guide: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

3. The programs are in Synaptic manager, they are all for Ubuntu. If you whant something extra, you need to check at the program's site or something like that. Check this site too [http://linuxappfinder.com/multimedia](http://linuxappfinder.com/multimedia)

Enjoy.:-D

---

### Post by movietrailer on 2007-01-19
I'm not sure what more information would be needed about the wireless bit.
I try to push the button on, but it doesn't light up like it does in windows.
Ususally, it'll flash on and off until it finds a network, then stay on when connected.
I have an Acer Aspire 3610 notebook, but I'm not sure how to find out what the name of my wireless card is...

---

### Post by raul_ on 2007-01-19
Wireless support is good with Linux because ndiswrapper uses windows drivers. See if your wireless card is supported:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

---

### Post by pebo on 2007-01-19
To find which wireless card you have open a terminal (Applications->Accessories->Terminal) and type```
lspci | grep Network
```

---

### Post by movietrailer on 2007-01-19
Ok I typed that in and got this
0000:06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)
So, do I search for that, or what?

And also, the answer for more space was to re-install?

---

### Post by IT'5Huxley on 2007-01-19
Try looking at this

[http://www.linuxquestions.org/questions/showthread.php?t=444187](http://www.linuxquestions.org/questions/showthread.php?t=444187)

---

### Post by sloggerkhan on 2007-01-19
to get more space, reinstall and choose a different drive to install to. (It is an option somewhere in the process.)

To get your wireless working:
[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

---

### Post by pebo on 2007-01-19
> **IT'5Huxley said:**
> Try looking at this

[http://www.linuxquestions.org/questions/showthread.php?t=444187](http://www.linuxquestions.org/questions/showthread.php?t=444187)
...[this ]("http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318") might help too :)

---

### Post by mikewhatever on 2007-01-19
> **movietrailer said:**
> 

And also, the answer for more space was to re-install?

It is really up to you, but perhaps you'd like to copy the entire partition.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by candtalan on 2007-01-19
> **movietrailer said:**
>  and I have another drive where there's alot of space. I would have put it there, but wasn't given the option

I do not understand why you were not offered an option for install to either of your drives - similar to ('Select a disk')
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

