---
title: "connect with modem to internet"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by brocolie on 2006-04-28
hi

it's now the first time i used ubuntu .. i liked the layout and was able to move around a little bit. my problem, i can't connect to the internet ](*,) and i am not sure where to set up the connection - i use a kflex 56 modem ...dont laugh, not everyone has broadband or dsl ...

if any one can help me, i am very thankfull. :KS 

regards  brocolie

---

### Post by gondilon on 2006-04-28
a dial-up modem is very hard to set up in linux. You can first try to configure it by going to networking preferences and click on the modem and click on properties.  If it is not supported, you will need to fidn a linux driver for it. I wish you luck.

---

### Post by gr0kzer0 on 2006-04-28
Thereis a graphical tool under System > Administration > Networking. But I'm not a fan of graphical interfaces and never bothered to figure it out. I prefer wvdial, a command line tool that is, I believe, included with Ubuntu as standard.

In a terminal, type

```
sudo wvdialconf /etc/wvdial.conf
```

This will scan your system for working modems, and create a configuration file at /etc/wvdial.conf. This file will look similar to this:

```
[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
; Username = <Your Login Name>
; Password = <Your Password>
```

Use an editor to edit this file, supplying the dialup phone number for your ISP, username and password. Now, the command

```
sudo wvdial
```

should make your computer dial through to your ISP and make the connection. If successful, you'll get some output displayed, then it'll stop and appear to hang. The computer is waiting for you to use the connection. Switch to a different terminal and give the command

```
ping -c1 80.84.72.25
```

If you get output like this:

```
PING 80.84.72.25 (80.84.72.25) 56(84) bytes of data.
64 bytes from 80.84.72.25: icmp_seq=1 ttl=45 time=767 ms

--- 80.84.72.25 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 767.244/767.244/767.244/0.000 ms

```

congratulations! You're online!

When you're finished with your online session, return to the terminal where you gave the "sudo wvdial" command, and press Ctrl+C. This will end the connection, making wvdial hang up.

If the command "sudo wvdial" didn't result in a connection being made, read through the output. There'll be some info there that'll be helpful when troubleshooting.

Read the manpages for wvdial, wvdialconf and wvdial.conf.

---

### Post by az on 2006-04-28
[QUOTE=brocolie]hi

it's now the first time i used ubuntu .. i liked the layout and was able to move around a little bit. my problem, i can't connect to the internet ](*,) and i am not sure where to set up the connection - i use a kflex 56 modem ...dont laugh, not everyone has broadband or dsl ...

if any one can help me, i am very thankfull. :KS 

regards  brocolie[/QUOTE]

It's hard to tell whether you have a hardware modem or a software modem.  Kflex is a protocol, not a chipset.  Is it an internal modem or an external one?


Software modems need drivers to work.  Most softwa«re modems have driver for linux, but they are not distributed with the OS.

---

### Post by Lin-X on 2006-05-15
I have a dial-up and a win modem.

My dial-up is a serial modem: DiamondSupraExpress 56k, that I bought on E-Bay for $17. I have been able to configure it easily in Administration-Network-Modem Connection. ... But only in Ubuntu. For some reason I can't get this thing to work in
Knoppix, Damn Small Linux, Suse. I have no idea why, but these all use KDE desktop. On the other hand, I had it working with KDE in Xandros Desktop 3.0. Duh ...  Anyway, if what you have is an external modem, keep looking; you CAN get it run
ning. (I have even used mine from the Ubuntu live cd!)

As for Winmodems, if you have one, find out what kind it is and then go to Linmodems.com ( I think that's the correct name; Google it if you have to, of course.) You may have to download a driver and install it; on the other hand, please be aware that the previous kernal --- not sarge but the *.4) could handle some Winmodems out of the box, so to speak.

I hope this post was not confusing or unhelpful. I have had PULENTEE of problems getting all my hardware working in Linux. I'm not a programmer, a hacker or a geek; all my advice is from experience. If you keep trying and ask the right ques-
tions, you will find your answer. The people on this forum are just awesome!

---

