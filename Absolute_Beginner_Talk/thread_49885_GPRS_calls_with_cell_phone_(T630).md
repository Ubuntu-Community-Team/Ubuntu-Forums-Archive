---
title: "GPRS calls with cell phone (T630)"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-18
Oh bugger me again!!!

Just searched the forums for info on setting up GPRS, but came up with nothing helpfull. 

I recall once reading a post of setting up GPRS on a SE T630, but I cannot find it for the life of me. Anyone have it?

I've got my phone happily chatting with Bluetooth to my PC now, but when I tried to set up internet, I was asked for a dial-up number. 

Well, GPRS don't use dial-up numbers. The init string in my case is *99***1#, then the phone does the rest. Passwords, IP, usernames, APN the lot is kept by the phone, I just have to initialise the string. But there is no choice in my modem I need or want to use.

Anybody with relevant info?

NB>>>> I do not have ANY internet with Linux until I get past this problem. So please no "apt-get" 's for me! Give me the package names if you please.

---

### Post by GrootBrak on 2005-07-19
[QUOTE=GrootBrak]Oh bugger me again!!!

Just searched the forums for info on setting up GPRS, but came up with nothing helpfull. 

I recall once reading a post of setting up GPRS on a SE T630, but I cannot find it for the life of me. Anyone have it?

I've got my phone happily chatting with Bluetooth to my PC now, but when I tried to set up internet, I was asked for a dial-up number. 

Well, GPRS don't use dial-up numbers. The init string in my case is *99***1#, then the phone does the rest. Passwords, IP, usernames, APN the lot is kept by the phone, I just have to initialise the string. But there is no choice in my modem I need or want to use.

Anybody with relevant info?

NB>>>> I do not have ANY internet with Linux until I get past this problem. So please no "apt-get" 's for me! Give me the package names if you please.[/QUOTE]
 I wrote a small scripts last night that seems to work. At least it comes to the point where its dailing via bluetooth, which work great. But then I get a "script failure." I have tried various settings to get it going properly, but nothing. 

The scripts was added to Peers and Chatscripts. In fact I wrote about 5 different ones and used the "pon" command.  Anyone please with more info?

---

### Post by steffen on 2005-07-19
Have you tried GPRS Easy Connect? 

[http://easyconnect.linuxuser.hu/modules/index/](http://easyconnect.linuxuser.hu/modules/index/)

---

