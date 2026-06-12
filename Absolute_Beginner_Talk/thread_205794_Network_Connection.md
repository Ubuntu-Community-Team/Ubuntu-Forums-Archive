---
title: "Network Connection"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by timmahhny on 2006-06-29
Hello I am new to linux and have tried several different distros, and so far UBUNTU is a success where the others have failed.
I have an old laptop and I am attempting to connect to my network and internet using wireless pcmcia card. 
 The drivers are installed and the card is activated but the network connection is connected to "lo". I have tried everything that I can think of to change the connection to the linksys wireless which it sees, but it does not seem to be able to connect to. 
 How do I get into the network connection and configure the linksys network?
Thanks in advanced for your help
Tim

---

### Post by x64Jimbo on 2006-06-29
How do you know that the system sees the linksys card? When you're only showing "lo" that typically means that your system doesn't see the network card. lo is the loopback device that makes localhost and 127.0.0.1 work. 
To check if your system sees your device, try running this command
sudo lspci | grep linksys
that should return any output from the lspci program that contains the word linksys, which should tell you if your system has recognized the device. 
next, do:
ifconfig -a
If you only see "lo" your system is not picking up the hardware and you should probably look into using NDISWrapper with the windows drivers for the card.

---

### Post by timmahhny on 2006-06-29
Thank you for your quick post.
 
The reason why I say that it can see it is that under Network settings, It has my card and when you click on the properties button, it shows linksys with the radio signal along the side and in the Network Tools - Devices i shows under Network Device, lo and eth0 which is the linksys.
 
[COLOR=darkred]But I can't seem to get it into the network connection to make any changes.[/COLOR]
[COLOR=darkred]I ran what you said, sudo lspci | grep linksys and nothing came back.[/COLOR]
 
I know that it sees it because last night I ran something, can't remember and it showed the card, Belkin FD506020 card, atmel_cs and a whole bunch of other information. 
 
Sorry for the lack of information, tired and since I have tried many different things I am really confused on what I tried gave what informaiton. I will make it a point to write things down from now on.
 
Tim

---

### Post by timmahhny on 2006-06-29
X64Jimbo thanks for your quick reply.
I did some more reading on this in these forums and download WiFi Radar which sees the linksys nework, but it can't connect to it.
Does this mean that it is the driver for the card? The card (Belkin FD506020 ver 2) lights up, and the one light is blinking while the computer is attempting to connect.

 I read other posts and my router is set correctly, at least to what the posters are claiming will work.

I will continue to look at other posts and am currious to what your input will be. I still believe, and I have been wrong too many times in the past, but I do believe that the drivers are installed and working, it is just a matter of some how configuring the network connection with the eth0 (pcmcia card / linksys) and that is something I am very much in the dark on how to do.
Take care and thanks once again for your quick reply
Tim

---

### Post by timmahhny on 2006-06-29
X64Jimbo this is what I have when I ran iwconfig:

lo no wireless extensions

 eth0 IEEE 802.11-DS  ESSID: "linksys"
 Mode:Managed Frequency:2.437 GHZ  Access Point: 00:12:17:1C:46:AE
Bit Rate 11 Mb/s
Retry min limit 7  RTS thr:off Fragment thr:off
Power Management:off
Link Quality: 0  Signal level:0 Nosie level: 0
Rx invalix nwid:0 Rx invalid crypt: 0Rx invalid frag: 0
Tx excessive retries: 0 Invalid misc:1 Missed beacon:0
sit0 no wireless extensions

This is what I get, does it make any sense to you? Does it help?
Thanks
Tim

---

