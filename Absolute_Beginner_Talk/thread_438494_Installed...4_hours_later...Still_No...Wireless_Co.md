---
title: "Installed...4 hours later...Still No...Wireless Connection..."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Average_Jake on 2007-05-09
So just installed "ubuntu 6", now need to connect to my wireless internet...

Followed the "connect to wireless internet" instructions and kind feel like a fool for not getting this done in 4 hours.

[COLOR="Plum"]To do this, open System > Administration > Networking. If you can see a "Wireless Connection" entry under the Connections tab, then you may have a working driver already installed and simply need to activate the card. Select the entry and click on the "Properties" button to the right. Check "Enable this connection" and fill in the appropriate information below (SSID, network name, passcode, and connection settings). When finished, click OK and wait for the system to activate your card. If this does not produce a working connection, make sure you have entered all settings correctly, then consult the remainder of this guide to track down your problem(s).[/COLOR]

ok so i check the remaining parts...says something about installing ndiswrapper....which i find and attempt to install...with something called "synaptic"...ok....not able to install it (tar.gz file), until i get the "build-essential_11.1_i386 installed which is apparently is installable via "synaptic" but alas a search shows nothing through synaptic.  So i go to a site and download it, its in a ".deb" format...so i learn how to install it...but i get an error..."its not satisfieable" apparently...not sure what that means, but my needs are simple.

I'm just looking to get my wireless connection set up, and then i can deal with any other problems.  Can any one help?

---

### Post by Seisen on 2007-05-09
Do you have any kind of internet connection at all?

---

### Post by Average_Jake on 2007-05-09
I have two computers...1 can log in no problem, the second can not...i've been up and down ebuntu help forums and really getting fustrated

[COLOR="Pink"]network:1 DISABLED (that cant be good)
Wireless interface
BCM4306 802.11b/g wireless lan cntroller
Broadcom Corporation

iwconfig

lo : no wireless extensions
eth0 :no wireless extenstions
eth1 : IEEE 802.11b/g ESSID:"XXXXX" 
Access Point: Invalid

Sit0 : no wirless extensions
[/COLOR]

Does this help?

---

### Post by Average_Jake on 2007-05-09
I did everything on this page link: [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")

---

### Post by Seisen on 2007-05-09
Try this and see if it helps
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by LollYouSuckZor on 2007-05-09
> **Seisen said:**
> Do you have any kind of internet connection at all?

Let's just say if he didn't, would he have posted this?

Unless he was at.. a library or something..

---

### Post by Seisen on 2007-05-09
Ya, people do it all the time from their friends computers, from Windows.

---

### Post by Average_Jake on 2007-05-09
ok, i'll try that right now

---

### Post by decal on 2007-05-09
I own a dell laptop 1405 with wireless g capabilities. I'm new to Ubuntu and run a dual boot of Windows XP and Ubuntu. The only problem i have is that Ubuntu wireless doesn't work for me either. Anybody else with a dell have this same issue? I put the SSID in and it still won't connect. Also tried rebooting the router and laptop numerous times. My wireless works like a charm in XP so I know its a problem with ubuntu talking to my Linksys router.

Anybody have a dell laptop resolve this problem?

---

### Post by Average_Jake on 2007-05-09
Yeah, my computer is a dell (inspiron 600m) aswell, i tried all of the above to no avail - im also using a linksys router

---

### Post by Average_Jake on 2007-05-10
This sucks :( 

Here is a link that might be helpful, apparently this is a very common problem over 50 pages of commentry:

[http://ubuntuforums.org/showthread.php?t=25683]("http://ubuntuforums.org/showthread.php?t=25683")

---

### Post by Average_Jake on 2007-05-10
Here's my info if this helps:

lspci

0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

ndiswrapper -l

Installed ndis drivers:
bcmwl5a         driver present, hardware present


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"connect"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:C5:DF:31
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7304 (7.1 KiB)  TX bytes:7304 (7.1 KiB)

---

