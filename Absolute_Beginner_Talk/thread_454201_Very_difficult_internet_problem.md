---
title: "Very difficult internet problem"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by persofi on 2007-05-25
Hey folks,
I have a very difficult internet problem. Probably not solvable under Ubuntu, but I'd appreciate any attempt to help.

I connect to the internet over eth0 to some university server. Actually it's some kind of server in the dormitory which then connects to the university server I guess. Unfortunately, I dont really know anything how this network is setup. Here is however what I need to do to get it to work under windows:

1) In "Network Settings" - "TCP IP"  I have to do "Use following IP address" and "following DNS address" and enter some specific numbers.
2) In "Mozilla Firefox" I have use the "Standard Gateway" from step 1) as standard proxy for everything under Port 8080.
3) Everytime I want to open a website, I get asked for my university password and username.

Probably the network has some bugs or something, because Mozilla Firefox is the only program that works, not even Internet Explorer does that!

What could I try to do, to make it work under Ubuntu? Using the same Firefox settings and manually putting in the same IPs as under Windows in the network configuratino thing didnt work.

-persofi

---

### Post by Happy_Man on 2007-05-25
Have you opened network settings and tried to set up the proxy through there?

---

### Post by dstew on 2007-05-25
What version of Ubuntu do you have? What is the output of the command **ifconfig** entered in the Ubuntu terminal command line?

---

### Post by Carlos Santiago on 2007-05-25
Have you tried the network panel?
Well, by a command line it is easy. Just type:

sudo ifconfig <your interface, usually eth0 or eth1> <your IP>  netmask <your mask, usually 255.255.255.0> up.
Example:
sudo ifconfig eth0 192.168.99.35 netmask 255.255.255.0 up


Now setup the gateway
route add 0.0.0.0 mask 0.0.0.0 <IP of the gateway>

Example:
route add 0.0.0.0 mask 0.0.0.0 192.168.99.1

Test it with: ping <IP of the gateway>


Now setup the DNS.
In the /etc/resolve.conf file, add the line

nameserver      <DNS server>

Example: nameserver      143.100.101.102

To edit the file, type 
sudo gedit /etc/resolve.conf

Test it with ping [www.google.com](www.google.com)

Now just configure Mozilla, that should be equal to windows

---

### Post by persofi on 2007-05-26
Thx for your responses. I appreciate it very much!

1) I'm running Ubuntu Feisty btw with all the updates that were available ~1.5 weeks ago. The only application I installed that could possibly mess up network settings is WINE (could be wrong about that). I also have a wlan card that I'm not sure how to deactivate, could that maybe cause the problems?

2) The "ifconfig" command gives me this:  (I'm not running the english version of Ubuntu... I tried to translate some of the maybe relevant stuff in brackets)

----------------------------------------------------------------------------------------------------------------------------------

eth0      Protokoll:Ethernet  Hardware Adresse 00:0F:B0:F0:5A:DE  
          inet Adresse:141.201.189.150  Bcast:141.201.189.255  Maske:255.255.255.0
          inet6 Adresse: fe80::20f:b0ff:fef0:5ade/64 Gültigkeitsbereich:Verbindung [Validity area = connection]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000  [send wait length = 1000]  
          RX bytes:39994 (39.0 KiB)  TX bytes:492 (492.0 b)
          Interrupt:21 

eth1      Protokoll:Ethernet  Hardware Adresse 00:13:02:0F:FC:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Basisadresse:0x8000 Speicher:d0100000-d0100fff 

eth1:avah Protokoll:Ethernet  Hardware Adresse 00:13:02:0F:FC:48  
          inet Adresse:169.254.5.157  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Basisadresse:0x8000 Speicher:d0100000-d0100fff 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine  [validity area = machine]
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:29676 (28.9 KiB)  TX bytes:29676 (28.9 KiB)

----------------------------------------------------------------------------------------------------------------------------------

I had already tried to setup the proxy in the network settings. Now I used Carlos Santiagos instructions and this is what happened:

1)   sudo ifconfig eth0 --> seemed to work just fine
2 ) route add --> didnt work,  gave me this:

----------------------------------------------------------------------------

Benutzung: inet_route [-vF] del {-host|-net} Ziel[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Ziel[/Prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Ziel[/PrÃ¤fix] [metric M] reject
       inet_route [-FC] flush      NICHT unterstÃ¼tzt  [ NOT supported]

------------------------------------------------------------------------------

PING of course didnt work:

------------------------------------------------------------------------------
"PING 141.201.104.104 (141.201.104.104) 56(84) bytes of data.
From 169.254.5.157 icmp_seq=1 Destination Host Unreachable
From 169.254.5.157 icmp_seq=2 Destination Host Unreachable
From 169.254.5.157 icmp_seq=3 Destination Host Unreachable"
-------------------------------------------------------------------------------

3)  The sudo gedit /etc/resolve.conf   seemd to work just fine. One thing that confused me: The file was totally empty! Why is that? Like I said I previously tried to configure everything through the network manager. Thus I already entered a DNS server and it showed up in the configuration menu. Wasnt this supposed to be in the file?

---

### Post by dstew on 2007-05-26
Sometimes a problem like this can be from the ipv6 protocol interfering with the function of a server or router. You can disable ipv6 by editing the file **/etc/modprobe.d/aliases**. Change the line **alias net-pf-10 ipv6** to **alias net-pf-10 off**. See if that helps.

---

### Post by persofi on 2007-05-30
Hi,
disabling ipv6 didnt seem to have any effect. I (stupidly) opened and saved the "aliases" file with openoffice, could that have corrupted the file structure anyhow? Because on startup I get tons of error messages because of an invalid line in modprobe/aliases...
There is also some message about network problems in startup.

Is there any way to get the contents from the startup messages? Then I could post it here, which would probably be more helpul.

---

### Post by persofi on 2007-05-31
Hey folks,

Do you think I could solve my problem by installing VMware or VirtualBox under Ubuntu and running Windows XP under that? I mean the hardware seems to be recognized, it is a software linux error, which maybe could be solved by this.
Does this have any chance of working? Please tell me what you think, installing this stuff is very difficult for me, since I dont have internet under Ubuntu and dont really know much about Linux.

---

### Post by dstew on 2007-05-31
If you used Open Office to edit your /etc/modprobe.d/aliases file, that would cause your error messages. Try to recover it by saving it in plain text. It is always a good idea to make a backup before editing any configuration file (**mv configfile configfile.bak**) or something like that just to be safe. Sorry I didn't advise you about that.

To look at boot messages, use the **dmesg** command. You can also look at the boot log files. They are held in the /var/log directory. Two of the important logs are boot and syslog. Look at them using the **less** command so you can page back and forth (**less boot** or **less syslog**)

I think your problem is one of configuration. The hardware is probably OK. If you have a wireless card, it might be best to deactivate it and try to get connected through eth0 only. You should be able to do those things using Network Settings on the desktop. It might work also through virtualization of XP, but I think you should keep trying in Linux. Maybe put a new thread in the Networking and Wireless forum.

---

### Post by kernel tom on 2007-05-31
> **persofi said:**
> Hey folks,
I have a very difficult internet problem. Probably not solvable under Ubuntu, but I'd appreciate any attempt to help.

I connect to the internet over eth0 to some university server. Actually it's some kind of server in the dormitory which then connects to the university server I guess. Unfortunately, I dont really know anything how this network is setup. Here is however what I need to do to get it to work under windows:

1) In "Network Settings" - "TCP IP"  I have to do "Use following IP address" and "following DNS address" and enter some specific numbers.
2) In "Mozilla Firefox" I have use the "Standard Gateway" from step 1) as standard proxy for everything under Port 8080.
3) Everytime I want to open a website, I get asked for my university password and username.

Probably the network has some bugs or something, because Mozilla Firefox is the only program that works, not even Internet Explorer does that!

What could I try to do, to make it work under Ubuntu? Using the same Firefox settings and manually putting in the same IPs as under Windows in the network configuratino thing didnt work.

-persofi

I had the same problem, but my university server was WPA2 secured, so I could log onto firefox but navigating the web was a pain... see if you can find any "geek" site by ur school of guys that use linux... They might even have a completed wpa_supplicant.conf file that you can load through the command line that will bind you to the network everytime you run it, and keep you logged in

this is only if u have WPA security which is a very likely case with university internet

---

