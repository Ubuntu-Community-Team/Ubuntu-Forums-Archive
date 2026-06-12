---
title: "Installed Ubuntu, now how do I get internet to work?!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-06-12
I accidentaly posted in the wrong section: [http://ubuntuforums.org/showthread.php?t=471949](http://ubuntuforums.org/showthread.php?t=471949)

This is a very beginner question. Mods, please delete the thread linked to above.

"Ok, I am really not so tech savvy.

I have an actiontec router. I connected it from the router to the laptop (ubuntu) using a wire. The icon on the top connects and establishes. I open firefox, and can't browse the net. Any ideas what on earth is goin' on?"

---

### Post by phr0ze on 2007-06-12
Please open a terminal window and run ifconfig
Post the output back here.
Thanks

---

### Post by ajskhan on 2007-06-12
Umm... sorry - how do I do that? What is a terminal window?

I am guessing it is like the command prompt of linux? How do I get there...

EDIT: FOUND IT

---

### Post by starcraft.man on 2007-06-12
> **ajskhan said:**
> Umm... sorry - how do I do that? What is a terminal window?

I am guessing it is like the command prompt of linux? How do I get there...

Push Alt + F2 (this is the run prompt) then type in "gnome-terminal" and push enter. Then put in "ifconfig" and run it, and copy and paste output.

Alternatively, the terminal is in Applications > Accessories > Terminal.

---

### Post by ajskhan on 2007-06-12
hold
pls

---

### Post by ajskhan on 2007-06-12
> **ajskhan said:**
> hold
pls

ok i did it, and saved it in the office apps.

i attached it

---

### Post by starcraft.man on 2007-06-12
> **ajskhan said:**
> ok i did it, and saved it in the office apps.

i attached it

In future, please just post it in a reply and since its lines of text, use the ```
 tags.

This is whats in the file he attached folks:

[CODE] ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2 
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10506 (10.2 KiB) 

eth0:avah Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          inet addr:169.254.4.128  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:9324 (9.1 KiB)  TX bytes:9324 (9.1 KiB) 
```

Not everyone uses OO and also posting it maximizes the number of eyes seeing it.

---

### Post by ajskhan on 2007-06-12
Ok sorry, I didn't know how to change the format. What does it tell y'all?

---

### Post by ajskhan on 2007-06-12
no response?

---

### Post by crane on 2007-06-12
Is this a wireless connection? Try iwconfig and post if it is.
I would see if you can compare your settings to the router or another computer. Make sure the subnet and the gateway are set correct.

---

### Post by ajskhan on 2007-06-12
> **crane said:**
> Is this a wireless connection? Try iwconfig and post if it is.
I would see if you can compare your settings to the router or another computer. Make sure the subnet and the gateway are set correct.
It is WIRED. And how do I see if the subnet, and gateway are set correctly?

---

### Post by ugm6hr on 2007-06-12
How do you set up your router?  Most have a web address for setup e.g. 192.168.0.1 - try typing that into Firefox to see if you are connected to the router.

Judging by the ifconfig - there is some traffic via eth0.

Do other computers connect to the internet via this router?

---

### Post by crane on 2007-06-12
I noticed your subnet was 255.255.0.0
Most routers I have set up. (which is not a whole lot) have a standard subnet of 255.255.255.0
 You can change the settings via GUI by going to system>administration>network in your menu.

---

### Post by ajskhan on 2007-06-12
> **ugm6hr said:**
> How do you set up your router?  Most have a web address for setup e.g. 192.168.0.1 - try typing that into Firefox to see if you are connected to the router.

Judging by the ifconfig - there is some traffic via eth0.

Do other computers connect to the internet via this router?

My router? It has a wire going to it from Verizon FIOS. 
That goes into an actiontec router. And from that I hooked up another wire that runs to the ubuntu laptop.
It also hooks up to 2 other computers (windows)

> **crane said:**
> I noticed your subnet was 255.255.0.0
Most routers I have set up. (which is not a whole lot) have a standard subnet of 255.255.255.0
 You can change the settings via GUI by going to system>administration>network in your menu.

GUI? I went to where you told me, but then I see "wired" and "modem." What should I change?

----------------
On a side note- THIS EXACT SAME CONFIG: laptop, router, wire, everything - connected while on Windows 2000. I have played with a lot of settings on ubuntu - what should the settings be at?

It does say "network connection established" so I guess it connects - but firefox doesn't get me anywhere!

I do APPRECIATE THE HELP!

---

### Post by ajskhan on 2007-06-12
And what exactly does this tell you? (ifconfig)

 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2 
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10506 (10.2 KiB) 

eth0:avah Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          inet addr:169.254.4.128  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:9324 (9.1 KiB)  TX bytes:9324 (9.1 KiB)

---

### Post by crane on 2007-06-12
so it says you have a connection but no firefox. Does apt work? Try typing sudo apt-get update. It will promt you for your password. If this connects then your connected to the internet but Firefox is not working right. 
Also try this in a terminal.
```
ping google.com
```
hit ctrl c to end it. If this connected then good. If it timed out then do this:
```
ping 64.233.187.99
 
```
again hit ctrl c to end it.
 then let us know if this timed out as well or connected.

---

### Post by crane on 2007-06-12
> **ajskhan said:**
> And what exactly does this tell you? (ifconfig)

 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2 
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10506 (10.2 KiB) 

eth0:avah Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          inet addr:169.254.4.128  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:9324 (9.1 KiB)  TX bytes:9324 (9.1 KiB)
inet addr:169.254.4.128 is the IP assigned to your computer from the dhcp server (probably your router)
If you can check the settings on another computer on the network you can compare and see if this is close.
Is this set up on your home network or somewhere else?
 As far as the network GUI controls you say you had a wired and modem? If you are getting your internat trhough the network then  just click wired the properties. This is where you can change some of your settings.

---

### Post by ajskhan on 2007-06-12
> **crane said:**
> so it says you have a connection but no firefox. Does apt work? Try typing sudo apt-get update. It will promt you for your password. If this connects then your connected to the internet but Firefox is not working right. 
Also try this in a terminal.
```
ping google.com
```
hit ctrl c to end it. If this connected then good. If it timed out then do this:
```
ping 64.233.187.99
 
```
again hit ctrl c to end it.
 then let us know if this timed out as well or connected.
[B]
 sudo apt-get update[/B]

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US

  Could not resolve 'security.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US

  Could not resolve 'us.archive.ubuntu.com'

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources

  Could not resolve 'us.archive.ubuntu.com'

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources

  Could not resolve 'us.archive.ubuntu.com'

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages

Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages

  Could not resolve 'security.ubuntu.com'

Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources

  Could not resolve 'security.ubuntu.com'

Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US

Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  Could not resolve 'security.ubuntu.com'

Reading package lists... Done

E: Some index files failed to download, they have been ignored, or old ones used instead.

ME:~$ **ping google.com**

ping: unknown host google.com

ME:~$ **ping 64.233.187.99**

PING 64.233.187.99 (64.233.187.99) 56(84) bytes of data.

From 169.254.4.128 icmp_seq=2 Destination Host Unreachable

From 169.254.4.128 icmp_seq=3 Destination Host Unreachable

From 169.254.4.128 icmp_seq=4 Destination Host Unreachable

From 169.254.4.128 icmp_seq=6 Destination Host Unreachable

From 169.254.4.128 icmp_seq=7 Destination Host Unreachable

From 169.254.4.128 icmp_seq=8 Destination Host Unreachable

From 169.254.4.128 icmp_seq=9 Destination Host Unreachable

From 169.254.4.128 icmp_seq=10 Destination Host Unreachable

From 169.254.4.128 icmp_seq=11 Destination Host Unreachable

From 169.254.4.128 icmp_seq=13 Destination Host Unreachable

From 169.254.4.128 icmp_seq=14 Destination Host Unreachable

From 169.254.4.128 icmp_seq=15 Destination Host Unreachable

From 169.254.4.128 icmp_seq=17 Destination Host Unreachable

From 169.254.4.128 icmp_seq=18 Destination Host Unreachable

From 169.254.4.128 icmp_seq=19 Destination Host Unreachable

From 169.254.4.128 icmp_seq=21 Destination Host Unreachable

From 169.254.4.128 icmp_seq=22 Destination Host Unreachable

From 169.254.4.128 icmp_seq=23 Destination Host Unreachable

From 169.254.4.128 icmp_seq=25 Destination Host Unreachable

From 169.254.4.128 icmp_seq=26 Destination Host Unreachable

From 169.254.4.128 icmp_seq=27 Destination Host Unreachable

From 169.254.4.128 icmp_seq=29 Destination Host Unreachable

From 169.254.4.128 icmp_seq=30 Destination Host Unreachable

From 169.254.4.128 icmp_seq=31 Destination Host Unreachable

From 169.254.4.128 icmp_seq=33 Destination Host Unreachable

From 169.254.4.128 icmp_seq=34 Destination Host Unreachable

From 169.254.4.128 icmp_seq=35 Destination Host Unreachable



--- 64.233.187.99 ping statistics ---

37 packets transmitted, 0 received, +27 errors, 100% packet loss, time 36030ms

, pipe 4








I bolded what I typed. what does it tell you?

---

### Post by crane on 2007-06-12
Well this tell us this is not an issue with Firefox. You have no internet connection. Again go to another computer on the network, or boot to or connect a windows or another known working box. Then check network setting and write them down. Be sure to note IP address, Gateway, Subnet (or subnet mask)
In windows just click start> run> type in **cmp** then when the terminal pops up type **ipconfig** (take note that in windows it's **ip**config and Linux it **if**config) This will list what you need to know.
 Is the computer your on a duel boot? if it is does windows work on the network when you boot to it?

---

### Post by ajskhan on 2007-06-12
> **crane said:**
> inet addr:169.254.4.128 is the IP assigned to your computer from the dhcp server (probably your router)
If you can check the settings on another computer on the network you can compare and see if this is close.
Is this set up on your home network or somewhere else?
 As far as the network GUI controls you say you had a wired and modem? If you are getting your internat trhough the network then  just click wired the properties. This is where you can change some of your settings.

It is through a router. no modem...

I checked my router and do not see this computer at all!

---

### Post by crane on 2007-06-12
OK so you are connecting through a dial up phone connection?

---

### Post by ajskhan on 2007-06-12
> **crane said:**
> Well this tell us this is not an issue with Firefox. You have no internet connection. Again go to another computer on the network, or boot to or connect a windows or another known working box. Then check network setting and write them down. Be sure to note IP address, Gateway, Subnet (or subnet mask)
In windows just click start> run> type in **cmp** then when the terminal pops up type **ipconfig** (take note that in windows it's **ip**config and Linux it **if**config) This will list what you need to know.
 Is the computer your on a duel boot? if it is does windows work on the network when you boot to it?

Not a dual boot (no clue what that is) but I over wrote windows.


Here is what CMD says (typo - not cmp)
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\MY USERNAME>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : home
        IP Address. . . . . . . . . . . . : 192.168.1.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\MY USERNAME>

---

### Post by ajskhan on 2007-06-12
> **crane said:**
> OK so you are connecting through a dial up phone connection?

No - verizon FIOS - FIBER!

---

### Post by ajskhan on 2007-06-12
> **ajskhan said:**
> Not a dual boot (no clue what that is) but I over wrote windows.


Here is what CMD says (typo - not cmp)
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\MY USERNAME>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : home
        IP Address. . . . . . . . . . . . : 192.168.1.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\MY USERNAME>


Ok - I suppose this is a step forward. I inserted this into the "static ip" thing on system > administrator > network

Except, for the ip address i put 192.168.1.7

and on my router page in internet explorer I saw

PC Name:	
Connection Type:	Ethernet
IP Address:	192.168.1.7


Good? But still no worky in firefox :(




EDIT:  tried to ping it from the internet explorer router address, it didn't work "test failed"

---

### Post by crane on 2007-06-13
So ifconfig on linux gave you 
> 
eth0:avah Link encap:Ethernet HWaddr 00:10:A4:86:19:3D
inet addr:169.254.4.128 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
and ipconfig on a windows bax gave you: 

> Connection-specific DNS Suffix . : home
IP Address. . . . . . . . . . . . : 192.168.1.5
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.1

if you will notice Linux is on a different subnet , with a differentbroadcast, and a different IP.

 If your connecting through a router to a DSL or fiber modem then your setting will be under wired and not modem.
 Do you have a network manager applet in the top right bar on your desktop? click it and check o see if it is set to automaticly configure or if it is set to manual.
Basicly you should just about match you windows config with the exception of the ip address. Your subnet should be 255.255.255.0 and your gateway should be 192.168.1.1

When you open network manager click wired  then properties. You should see a dropdown menu. make sure it is set to automatic configure (DHCP)  then restart the network.
```
sudo /etc/init.d/networking restart
```
 then do ifconfig again and see what your setting are now.

---

### Post by crane on 2007-06-13
> **ajskhan said:**
> Ok - I suppose this is a step forward. I inserted this into the "static ip" thing on system > administrator > network

Except, for the ip address i put 192.168.1.7

and on my router page in internet explorer I saw

PC Name:	
Connection Type:	Ethernet
IP Address:	192.168.1.7


Good? But still no worky in firefox :(




EDIT:  tried to ping it from the internet explorer router address, it didn't work "test failed"
If your setting a static setup be sure to change the subnet to 255.255.255.0 and your gateway to 192.168.1.1.
This will tell the computer where to go for internet.

---

### Post by ajskhan on 2007-06-13
> **crane said:**
> So ifconfig on linux gave you 
 
and ipconfig on a windows bax gave you: 


if you will notice Linux is on a different subnet , with a differentbroadcast, and a different IP.

 If your connecting through a router to a DSL or fiber modem then your setting will be under wired and not modem.
 Do you have a network manager applet in the top right bar on your desktop? click it and check o see if it is set to automaticly configure or if it is set to manual.
Basicly you should just about match you windows config with the exception of the ip address. Your subnet should be 255.255.255.0 and your gateway should be 192.168.1.1

When you open network manager click wired  then properties. You should see a dropdown menu. make sure it is set to automatic configure (DHCP)  then restart the network.
```
sudo /etc/init.d/networking restart
```
 then do ifconfig again and see what your setting are now.


I changed it to DHCP and I get the same thing.
I am under wired.
What is ROAM MODE?

I did some other research. I ran
**dhclient eth0**

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



can't create /var/lib/dhcp3/dhclient.leases: Permission denied

Can't create /var/run/dhclient.pid: Permission denied

drop_privileges: could not set group id: Operation not permitted



So know I am guessing that it is my router's problem?

---

### Post by crane on 2007-06-13
I am not sure what roam mode is. So if you changed it to automatic you ended up with the original settings in ifconfig? What about static settings? after setting everything, restarting the network still no go?
I believe the dhclient command needs to be run in with sudo.
```
**sudo dhclient eth0**
```

 I will be afk for a bit. I hope someelse can help you. if not. I will be glad to help further in a little while.

---

### Post by ajskhan on 2007-06-13
Ok, I am a bit frustrated as this was so easy in windows - just plug in. I got no go with either.

Would it be easier just to set up a PCMCI card? I have a wireless pc card from netgear MA521.

How do I set it up?


(and that sudo thing didn't work)

and the static thing doesn't even show a established connection thing.

---

### Post by crane on 2007-06-13
It can be a bit frustrating sometimes. If you have a wireless card I would deffinantly try it to see if it works.
This section if ifconfig:
```
eth0:avah Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          inet addr:169.254.4.128  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

```
looks strange to me. Mine does not come up like that. You could try searching the forums or Google for an expalination of why you have eth0:avah. That may lead to some insight as to why it's not working.
Maybe someone on the forums here could explain what that is.

 I did find one link here 
[http://ubuntuforums.org/archive/index.php/t-437248.html]("http://ubuntuforums.org/archive/index.php/t-437248.html")
if there is anyway to try a different network card that may be worth it as well. I'm guessing this is a laptop so changing the onboard network may not be an option.

---

### Post by ajskhan on 2007-06-13
Can anyone point me in the right direction for the card? I have a NETGEAR WIRELESS MA521 CARD which will connect to the Actiontec router. I have a driver but I am supposing it is for windows.


I did find this (but have no clue what on earth it means): [http://ubuntuforums.org/showthread.php?t=92119](http://ubuntuforums.org/showthread.php?t=92119)

And I did find something about ndiswrapper - again, no clue what it means!

and realtek, but don't know what that is either

---

### Post by crane on 2007-06-14
**Bunp***

Sorry I do not have any experience with using ndiswrapper. Maybe someone will offer some insight.

---

### Post by ajskhan on 2007-06-14
Mr Crane, I appreciate your help. I ended up using my MA101 router (which surprisingly, worked as soon as I plugged it in!).

---

### Post by crane on 2007-06-16
So this was an issue caused by the router? Interesting. If you don't mind me asking, what is the output of ifconfig now?

---

### Post by ajskhan on 2007-06-16
ok

ifconfig
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:A4:86:19:3D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask: 255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:46:24:72  
          inet addr:192.168.1.7   Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe46:2472/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1 
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2006 (1.9 KiB)  TX bytes:1565 ( 1.5 KiB)



btw, I still think it is a ubuntu prob, cuz it worked flawlessly in windows- not to be critisizing

---

