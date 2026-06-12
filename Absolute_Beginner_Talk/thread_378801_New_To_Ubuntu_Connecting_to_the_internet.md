---
title: "New To Ubuntu: Connecting to the internet"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by JakeTFG on 2007-03-07
This is a great operating system however one major problem I am having is that I can not connect to the internet. When i plug my ethernet cable into my box, it does not read it under netwokring.

Thanks for teh help. :popcorn:

---

### Post by overdrank on 2007-03-07
> **JakeTFG said:**
> This is a great operating system however one major problem I am having is that I can not connect to the internet. When i plug my ethernet cable into my box, it does not read it under netwokring.

Thanks for teh help. :popcorn:

Hi welcome to ubuntu! Could you tell us about your system and we can help. Like the version of ubuntu you are using. 6.06 dapper 6.10 edgy?:)

---

### Post by JakeTFG on 2007-03-07
Brand Name: HP
80 GB Hardrive
256 MB RAM
Intel Pentium 4
Unbuntu: 6.06 LTS

---

### Post by Matt1632 on 2007-03-07
Try restarting ubuntu with the cable plugged in, that worked for me.

---

### Post by JakeTFG on 2007-03-07
^ not for me :( tried turning it off then restarting, didnt come up with the connection.

---

### Post by tears.of.angels on 2007-03-07
if you're in GNOME, try settings>network connections (it might be setting, or administration)

network ought to be there somewhere. from there you can click on the check boxes for the network cards in your system.

keep in mind some devices (such as wifi or modem) need to be configured under properties.
LAN shouldn't need to be, but check there (also if it needs a static IP)

---

### Post by J11Gyro on 2007-03-07
I had same problem and since I had just loaded the OS I reloaded it with the cable plugged in and whoa it found the net and all on its own.

---

### Post by igknighted on 2007-03-07
> **JakeTFG said:**
> ^ not for me :( tried turning it off then restarting, didnt come up with the connection.

What type of connection is it (cable/dsl/etc.)?  Are you using DHCP or do you need to define a specific IP address?  Are you going through a router?  A proxy?

---

### Post by JakeTFG on 2007-03-07
Cable Internet (10 MPS - Boston - RCN) via ethernet and router provided by the cable company.

Only 2 things come up in the GNOME settings> network

A modem and some land line thing?

---

### Post by mkjarema on 2007-03-07
This happened to me, and I installed Edgy a few times, in the network settings, you are probibly defaulting to the "lo" option, which is looping you. A drop down is available that will alow you to select eth0 (I believe) That selects the ethernet option and wireless is eth1 (but another ball of wax)

I wish I could be more specific on telling you how to get there other than this.  ON your top panel, there is a double computer icon.  Click it and it is the "connection properties" window, use the drop down in the general tab to select eth0 instead of lo

hope this helps :-/

---

### Post by JakeTFG on 2007-03-08
I cant seem to find it, heres a picture:
[IMG]http://i17.tinypic.com/42jj3fm.png[/IMG]

---

### Post by JakeTFG on 2007-03-08
> **mkjarema said:**
> This happened to me, and I installed Edgy a few times, in the network settings, you are probibly defaulting to the "lo" option, which is looping you. A drop down is available that will alow you to select eth0 (I believe) That selects the ethernet option and wireless is eth1 (but another ball of wax)

I wish I could be more specific on telling you how to get there other than this.  ON your top panel, there is a double computer icon.  Click it and it is the "connection properties" window, use the drop down in the general tab to select eth0 instead of lo

hope this helps :-/

Havent even found where to find this >>

---

### Post by Bachstelze on 2007-03-08
Output of

```
sudo ifconfig -a
```

please ?

---

### Post by JakeTFG on 2007-03-08
> **HymnToLife said:**
> Output of

```
sudo ifconfig -a
```

please ?

What does that mean?

---

### Post by Bachstelze on 2007-03-08
Open up a [terminal](http://psychocats.net/ubuntu/terminal) and type - or copy/paste to avoid typos - the command I told you in it. It will prompt for your password and then output some text, which I'd like you to copy/paste here.

---

### Post by JakeTFG on 2007-03-08
jake@UnbuntuPwns:~$ sudo ifconfig -a
Password:
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:79:B5:27  
          inet6 addr: fe80::20c:6eff:fe79:b527/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1822 (1.7 KiB)  TX bytes:468 (468.0 b)
          Interrupt:185 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66772 (65.2 KiB)  TX bytes:66772 (65.2 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

note: internet not plugged in when i ran this, posting from my mac.

---

### Post by Bachstelze on 2007-03-08
What happens when you do this ?

```
sudo dhclient eth0
```

---

### Post by JakeTFG on 2007-03-08
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0c:6e:79:b5:27
Sending on   LPF/eth0/00:0c:6e:79:b5:27
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

---

### Post by GranpaDan on 2007-03-08
For me, as a beginner, the first thing I would back everything up and re-installing with the cable plugged in, and I would think the system would configure itself properly to your hi-speed connection. Maybe consider upgrading to 6.10.

---

### Post by JakeTFG on 2007-03-09
did that, still not reading the connection.

---

### Post by JakeTFG on 2007-03-09
Whats the point of an OS if you cant connect to the internet?

---

### Post by Bachstelze on 2007-03-09
What's the point of trolling besides making you look like an idiot ?

---

### Post by JakeTFG on 2007-03-09
Trolling? How is this trolling? is this not a place for new users of linux to get help with problems or is it a playground?

If you can not help, then you should not post garbage.

---

### Post by Bachstelze on 2007-03-09
> **JakeTFG said:**
> Whats the point of an OS if you cant connect to the internet?

This is definitely trolling since millions of people are connecting to the net with Linux. With such an attitude, no wonder people are not enthusiastic to help you...

---

### Post by JakeTFG on 2007-03-09
end of discussion

---

### Post by Bachstelze on 2007-03-09
All right, back on topic : how is your internet connection set up (cable or DSL ? router ?) Also, are you sure your network card is detected ?

---

### Post by JakeTFG on 2007-03-09
Cable Router (RCN 10 MBPS)

I am not quite sure if its decting the network card as in the screenshot i posted it only showed the modem and another LAN connection i believe.

---

### Post by Bachstelze on 2007-03-09
If you have a Windows running on that box, could you open a command-line (Start > Run > cmd) then run the command

```
ipconfig /all
```

and paste what you get ? That way, we'll know how Windows configures the network and we'll be able to configure Ubuntu the same way. To know if your network card is detected in Linux, run

```
lspci
```

---

### Post by JakeTFG on 2007-03-09
Problem solved. I'm posting from firefox in ubuntu right now :D

I was just unplugging the cable from my iMac and inserting it into my HP box. I had to turn off my modem, turn off the ubuntu, plug in the cable, plug in the modem and then start the computer up.

Now i can check out the cool video programs of ubuntu... maybe ill find something as alternative to Final Cut Pro as well i dont have $1200 :D

---

### Post by ComplexNumber on 2007-03-09
i wonder if the problem is caused by the DNS. when i installed dapper, it wouldnt allow me to connect to the internet unless i put in the DNS IP of of my ISP, so that it uses that instead of the DNS of the router(ie DHCP). 
edgy was fine, but dapper wasn't.

---

