---
title: "Connect to Comcast (agin!)"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by CapnChkn on 2007-09-14
[B][FONT=Times New Roman][SIZE=2]Hello Folks!

I've finally gotten enough stuff together to actually install and run Linux, I was told the Ubuntu would be the way to go.   To my delight, this form ([COLOR=Red]Release 7.04 feisty[/COLOR]) is REALLY easy!   I bought a copy of Corel Linux years ago and couldn't resolve any multi-boot issues.   Now I'm using two computers.

My problem is the old "no support" thingy from Comcast.  I've looked into the Interweb which brought me back here to Ubuntu, searched through the forums, and still no answer to this problem.

Strangely, on the P4 2.7 Ghz system I connected and surfed the web through an [COLOR=Red]Arris Touchstone TM402[/COLOR] using the "live CD" feature of the Distribution.  The install on an old IBM Netvista 2276 ([/SIZE][/FONT][FONT=Times New Roman][COLOR=Red]Intel PIII 733MHz, 256MB RAM, 20GB HDD, i810e Graphics Chipset[/COLOR]) recognizes the ethernet, but doesn't connect to Comcast.

[/FONT][/B]**[FONT=Times New Roman]I have tried connecting using Ethernet alone on the IBM and with the modem connected to both the IBM and my XP system with USB, which the documentation declares I can connect two computers with.  There is no change in the networking status.[/FONT]**
[B][FONT=Times New Roman] 
Following instructions I found on:

[/FONT][FONT=Times New Roman][http://ubuntuforums.org/showthread.php?t=450949&highlight=comcast](http://ubuntuforums.org/showthread.php?t=450949&highlight=comcast)

I come up with this bunch 'o stuff.
[/FONT][/B]> capnchkn@capnchkn-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:50:9B:BC:74  
          inet6 addr: fe80::211:50ff:fe9b:bc74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:711771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50993675 (48.6 MiB)  TX bytes:20393 (19.9 KiB)
          Interrupt:11 Base address:0x6f00 

eth0:avah Link encap:Ethernet  HWaddr 00:11:50:9B:BC:74  
          inet addr:169.254.7.183  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x6f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:179636 (175.4 KiB)  TX bytes:179636 (175.4 KiB)[B][FONT=Times New Roman]Where to now?
Cap'n!
[/FONT][/B]

---

### Post by bwhitaker on 2007-09-14
Looks like you aren't getting an IP address from DHCP, are you connecting straight to the cable modem with an ethernet cable?

---

### Post by Sayers on 2007-09-14
Comcast doesn't support linux?

---

### Post by Maestro23 on 2007-09-14
> **Sayers said:**
> Comcast doesn't support linux?

I've been running Linux on my system with Comcast Broadband for the past 2 years.  No problems.

---

### Post by CapnChkn on 2007-09-14
[B][FONT=Times New Roman][SIZE=2]Yep!  I'm connecting to the Modem with a Straight Ethernet Cable.  This computer is connected with a USB cable using the drivers I downloaded from [Arris]("http://www.arrisi.com/support/usb/index.asp") (I think).  I have reset the Modem several times, which is something I usually have to do when switching computers.
[/SIZE][/FONT][/B]

---

### Post by dndrich on 2007-09-14
OK, I'm guessing here, and I don't totally understand what you are trying to do, but let me tell you about what I know about Comcast, which may help.

Comcast security requires that the first time it is set up, it makes a record of the MAC address of the ethernet hardware.  So the usual story is that it is set up by ethernet or USB from the cable modem directly to the computer without a router.  I figured this out when I wanted to set up a wireless network for my brother.  Comcast wants you to use their residential gateway and services, for which they charge you.  OK, so, if you can reach the internet via a Windows machine, then look at the MAC address of that card.  Best way to go from here would be to use a router between the cable modem and the computer.  First, hook up the router, but not the cable modem, and hook the router to the computer that was able to connect to the internet before.  Now, in the router software that is reached by a web browser, you can clone the MAC address.  All modern routers let you do this.  Now, hook up the cable modem, and it thinks it is talking to the correct ethernet card, even though the router is fooling it.  Now, any computer can hook in, including Ubuntu based ones.  I think I read somewhere that Ubuntu shows a much longer MAC address than Windows does, and that the first 12 characters are the one's normally needed.  So it could be that in Ubuntu your cable modem thinks it has the wrong MAC address even though physically it may be the same ethernet card.  I have my brother's home network using Ubuntu through Comcast with no difficulty at all by this method.  I hope this helps.

---

### Post by CapnChkn on 2007-09-14
[FONT=Arial][B]I'm not sure either, I have connected this computer before using the same Ethernet card and Windows ME.  Usually I have to press the modem's "reset" button and the modem magically connex!

I have followed all the steps I've done before, with no result. Is there a method of getting the IP from DHCP?

I'm off to find a Linux driver for the NIC.  It isn't the browser...
[/B][/FONT]

---

### Post by SunnyRabbiera on 2007-09-14
well if it helps you might want to use the Ethernet connector as opposed to the USB as thats how I did it.
Personal question though, did you just recently get a new box from comcast?
if so make sure they registered it under your account, I had that issue a few months ago

---

### Post by voided3 on 2007-09-14
I just got an apartment in Boston and they use Comcast here. They do not support Linux to the best of my knowledge (the guy who came by to give me my modem never heard of it before), but if you open firefox and get the "your OS isn't supported" if you just got set up, they give you a phone number you can call so they can activate your modem. In other words, it's probably them, not your hardware unless the applet on the desktop can't connect at all or says there's nothing to connect with. By the way, I highly recommend either getting a wired or wireless router for security purposes since they create a subnet and act as a firewall.

---

### Post by dndrich on 2007-09-14
Definitely get a router to put between the modem and the computer.  They are really cheap, and offer better protection than software.  Even with only one computer, use a router.

---

### Post by deadgobby on 2007-09-14
I think using the USB is not helping much. All so changing between computers is not helping much. It may be telling Comcast server that there is a different IP addy. I had this problem when I bought a new PC with Mediacom. They had to reset the line and then every thing was fine. Getting a router is the best way to go. I have a Linksys wired BB router. While you are shopping around and want to save a couple of bucks off your bill. Pick up a Cable modem too. When you switch modems you will be calling up comcast to reset the line. I had to call up mediacom to reset when I pull out their modem with mine. Wired routers are not that much as WIFI ones. I am going to get a WIFI so my son can use the internet on is system. 
Peace
Gobby

---

### Post by Drakkor on 2007-09-14
i have Comcast HSI, a cable modem, and a dual boot Ubuntu/XP and never had any problems connecting to the net on either. :)

---

