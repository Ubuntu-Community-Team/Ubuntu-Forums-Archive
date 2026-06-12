---
title: "[SOLVED] Atheros Wireless Cannot Connect"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by primetime on 2007-07-18
Hey Guys.

I installed Ubuntu Feisty a few days ago on my Asus W3V Laptop.  So far the only thing that's keeping me from enjoying my new Linux system is that the wireless isn't working.

Basically, my wireless card is up, using the kernel modules 2.6.20.16-generic using the madwifi drivers.  It can detect networks so I know it's working.  However, I can't seem to connect to my access point.  Network Manager just keeps trying to connect to the AP.

The card is an Atheros 5006X Mini-PCI.  Using the Madwifi drivers in the restricted modules.

---

### Post by Fitzy_oz on 2007-07-18
> **primetime said:**
> Hey Guys.

I installed Ubuntu Feisty a few days ago on my Asus W3V Laptop.  So far the only thing that's keeping me from enjoying my new Linux system is that the wireless isn't working.

Basically, my wireless card is up, using the kernel modules 2.6.20.16-generic using the madwifi drivers.  It can detect networks so I know it's working.  However, I can't seem to connect to my access point.  Network Manager just keeps trying to connect to the AP.

The card is an Atheros 5006X Mini-PCI.  Using the Madwifi drivers in the restricted modules.
Try dropping to a command line and typing sudo dhclient wlan0 (or whatever interface your wifi card is setup as).  This might force it to obtain the address. 

Failing that, does your wireless network use WPA/WEP encryption - If so what is the key type?  I'm pretty sure it needs to be  set to Open system for it to function correctly... After which you should be prompted by the Network Manager to enter a key (be it a passphrase or a hex key).

---

### Post by primetime on 2007-07-18
Hey Fitzy,

Thanks for the reply.

Access Point Details:

WPA-TKIP, SSID Broadcast off (But I know I can detect it, based on my OpenSuse experience)
Normally, I just enter a passphrase to connect to the network.

Another thing I forgot to mention, I can connect to other networks that have no security enabled.

---

### Post by bradmayne on 2007-07-18
ok so here's the deal with madwifi.  

1. wpa support is sketchy.  try downloading madwifi tools from the synaptic package manager under system.

2. you have to enter the passphrase/code first. Then do dhclient ath0 (or whatever your ath is ath0 , ath1, etc etc)

3. you might as well do sudo su then having to keep typing sudo all the damn time for this too.  

4 im using madwifi right now and once you get it going you shouldn't have any problems!! 

5. do this command once you have the madwifi tools:    wlanconfig ath0 list scan, then do this command: iwconfig once you have entered the key in.  if your still having trouble i'll give you a quick walkthrough in the morning.  (it's like 2 am here) peace dude

---

### Post by primetime on 2007-07-18
Thanks for all your help guys.

So here's a little more info:

```

primetime@fiesty:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:A5:0E:42:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.0 KiB)  TX bytes:978 (978.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:14:A5:0E:42:40  
          inet addr:169.254.3.209  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:13:D4:E1:9A:7B  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fee1:9a7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:437474 (427.2 KiB)  TX bytes:48424 (47.2 KiB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5204 (5.0 KiB)  TX bytes:5204 (5.0 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-A5-0E-42-40-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16665 errors:0 dropped:0 overruns:0 frame:14856
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1470001 (1.4 MiB)  TX bytes:11096 (10.8 KiB)
          Interrupt:17 

primetime@fiesty:~$ 
```

dhclient Output:

```
There is already a pid file /var/run/dhclient.pid with pid 6065
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:a5:0e:42:40
Sending on   LPF/ath0/00:14:a5:0e:42:40
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

If there are any other things I can provide to aid in solving this problem..  just tell me :D

---

### Post by bradmayne on 2007-07-18
i've had that problem to concerning the output from your trying to use dhclient.  i'm sitting here trying to remember what i did to get a ip.  did you enter your wep or wpa key first?  hit me up. I'll check back in a few hours i gotta go to parole.

---

### Post by primetime on 2007-07-18
Hey brad.
Thanks for your help. 

I think the problem lies with network-manager... or somewhere in Ubuntu Feisty, it's using probably running two drivers.  because I have wlan and ath0 running it looks like based on the output of ifconfig

Edit:

Is there a way to disable the madwifi drivers in the restricted modules?  I tried running 'restricted-manager' and unchecking the 'enabled' box for the Atheros driver, but it still seems to be working.  

I was thinking, maybe there's a way to disable the restricted driver, and just using madwifi packages.

---

### Post by Fitzy_oz on 2007-07-18
> **primetime said:**
> Hey brad.
Thanks for your help. 

I think the problem lies with network-manager... or somewhere in Ubuntu Feisty, it's using probably running two drivers.  because I have wlan and ath0 running it looks like based on the output of ifconfig

Edit:

Is there a way to disable the madwifi drivers in the restricted modules?  I tried running 'restricted-manager' and unchecking the 'enabled' box for the Atheros driver, but it still seems to be working.  

I was thinking, maybe there's a way to disable the restricted driver, and just using madwifi packages.

You could blacklist one of the modules in modprobe.d, this will stop one of the modules from loading at boo.  Drop a to command line and type gksudo gedit /etc/mdoprobe.d/blacklist.  Then just add the module name of the driver you want to disable.

---

### Post by kevdog on 2007-07-18
Can you cut and paste the following output:
lshw -C network

Getting WPA working is a little tricky.  Can you first connect to an unencrypted network??  Have you downloaded the wpa-supplicant package?

---

### Post by primetime on 2007-07-18
kevdog:

Here's the output of lshw -C network
```
  *-network:0             
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:d4:e1:9a:7b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 duplex=full firmware=N/A ip=192.168.1.119 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fbffc000-fbffffff ioport:d800-d8ff irq:20
  *-network:1
       description: Wireless interface
       product: AR5006X 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@03:02.0
       logical name: wifi0
       version: 01
       serial: 00:14:a5:0e:42:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fbfe0000-fbfeffff irq:17
```

According to the Synaptic Package Manager, the wpasupplicant installed on my system is 0.5.7-0ubuntu2

I could connect to the unsecured networks near me.  But when I try to connect to my network, it doesn't work.  I tried to Enable Broadcast SSID on my router (I disable broadcast to help with security) which the card detects, but still no go.

Edit:

I noticed the logical name of the card is 'wifi0'.  In other distros I've tried, it's usually ath0.  Is there a way to change this?

---

### Post by kevdog on 2007-07-18
Ok it definitely looks like you are using the madwifi drivers for your card
> driver ath_pci

Good to know that you can connect with unencrypted networks (major plus on that!)

Good that wpasupplicant is installed.

Here is what I would try from command line.  We can automate the process with another program if everything works (ie network manager, wicd)

Create wpa_supplicant configuration somewhere, say, /etc/wpa_supplicant.conf. A simple configuration example:
 ```

gksu gedit /etc/wpa_supplicant.conf  <---This will open the editor
```

```

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="myssid"
   psk="mysecret"
   key_mgmt=WPA-PSK
   proto=WPA
 }
```

should suffice. Note that psk given above can be plain text ASCII pass phrase that is used on the AP or hex digits (without quotes) that can be generated with wpa_passphrase from the same ASCII pass phrase. For simplicity, go with ASCII pass phrase.

Above configuration causes wpa_supplicant to negotiate which encryption scheme to use. Certain AP’s might not work with this negotiation procedure. So it can help to limit the scheme to the most basic WPA one: TKIP. Add this line to your config to do so: pairwise=TKIP 

Now start the interface and then wpa_supplicant. For example, as

```
sudo ifconfig wlan0 up <---This may be wlan0, eth0, eth1, wifi0, ath0 depending on your interface
sudo wpa_supplicant -Dmadwifi -iwlan0 -c/etc/wpa_supplicant.conf -dd  <----Again wlan0 may be wifi0, ath0, etc
```

Pop open another terminal

```
sudo dhclient wlan0  <---Again wla0 may be wifi0, ath0, eth0, etc
```

---

### Post by bradmayne on 2007-07-18
hey about the wifi0 and ath0 they are both for madwifi. You need both of them.  Can you make sure your wireless router will allow dhcp?  Sometimes routers are configured to only allow certain MAC addresses.  Can you change your encryption key to WEP for the time being?  Let me know?  I will be on for awhile and you can im me: brdmayne           i use yahoo im.

---

### Post by kevdog on 2007-07-18
I think you can change your interface name wifi0-->ath0 by editing the /etc/iftab file.  You could post this file here if you need help.

---

### Post by bigboy_pdb on 2007-07-19
I tried to get my fiancee's wireless networking card which was an Atheros card and I had problems with it. I know that you can specify the encryption type but I found some really strange things occurring when I tried to use different options to set the encryption. Some would let me specify WPA while others would only let me use WEP.

My suggestion is that you could try changing your network to broadcast and then attempt to connect using the Wireless Manager. The reason why it may make a difference is because your card might detect what type of encryption it should use.

EDIT: If I remember correctly, changing the router so that it would broadcast the signal made a difference on her computer. The only problem is that it would always ask for the encryption key on startup and the keyring would also come up following that.

---

### Post by asgard123 on 2007-07-19
I have the same problem on my macbook pro. The debug output is the same as you have.

 I can connect if I disable athentication on the modem but otherwise ubuntu is trying to connect (I think via wep encryption) instead of WPA which all my other pc's use.



Since I am new to ubuntu I am not really sure... but it is a big problem.

---

### Post by primetime on 2007-07-19
> **bigboy_pdb said:**
> I tried to get my fiancee's wireless networking card which was an Atheros card and I had problems with it. I know that you can specify the encryption type but I found some really strange things occurring when I tried to use different options to set the encryption. Some would let me specify WPA while others would only let me use WEP.

My suggestion is that you could try changing your network to broadcast and then attempt to connect using the Wireless Manager. The reason why it may make a difference is because your card might detect what type of encryption it should use.

EDIT: If I remember correctly, changing the router so that it would broadcast the signal made a difference on her computer. The only problem is that it would always ask for the encryption key on startup and the keyring would also come up following that.

Hey Bigboy.

Thanks for your reply.

I did everything kevdog and brad suggested.

Right now I am posting from my wireless connection!  Booyah!  Thanks to all that helped.

I think the important factor in the solution was that the SSID had to be broadcast.  (Which is weird because when I was using OpenSuSE, the madwifi drivers did not need the SSID of my AP to be broadcast)

The keyring manager keeps popping up on startup though and aside from that, just like you said Bigboy, the connection keeps asking for the password/phrase... >_<  very annoying.. sigh. (if there's a way to change this... I'd appreciate it.)

---

### Post by primetime on 2007-07-19
> **asgard123 said:**
> I have the same problem on my macbook pro. The debug output is the same as you have.

 I can connect if I disable athentication on the modem but otherwise ubuntu is trying to connect (I think via wep encryption) instead of WPA which all my other pc's use.



Since I am new to ubuntu I am not really sure... but it is a big problem.

Hi asgard123,

Do you have SSID Broadcast Enabled on your router/AP?  Try Enabling SSID broadcast and then try to connect when network-manager (that icon on your taskbar) can detect your network.

---

### Post by asgard123 on 2007-07-19
Yep, I am following all the tips here now.. let you know in a tick how it goes.

Did you think it was a combination or is there one solution here that worked for you?

---

### Post by primetime on 2007-07-19
> **asgard123 said:**
> Yep, I am following all the tips here now.. let you know in a tick how it goes.

Did you think it was a combination or is there one solution here that worked for you?

I followed kevdog's walkthrough here:

[http://ubuntuforums.org/showpost.php?p=3042887&postcount=11](http://ubuntuforums.org/showpost.php?p=3042887&postcount=11) 
(I linked to the page so you can easily access it without the distraction of the other posts)

But it couldn't hurt to enable **SSID Broadcast** on your router.

My suggestion is, try enabling **SSID Broadcast** on your router first (if you have it disabled) and then try to connect using the network-manager.

If not, try kevdog's walkthrough. (with SSID Broadcast Enabled, just to play it safe ;))

Hope this helps!

---

### Post by kevdog on 2007-07-19
My walkthrough was simply that -- a test configuration.  Its wasnt meant to be a permanent solution, only to verify that indeed WPA would work if configured properly.  The next step was to make these steps into a more user-friendly configuration that wouldn't need to be typed anymore at the command line everytime to connect!

---

### Post by primetime on 2007-07-19
Oh!

So kevdog, what was the next step after checking the connection?

---

### Post by asgard123 on 2007-07-19
ok.. this does not work for me at the moment.

I need a few minutes to connect up somehow else so I can paste the output here..

Back soon

---

### Post by asgard123 on 2007-07-19
OK, I have been around the block with this and I could get nothing to work..

In the end I created another user so I logged on with a new profile and started fresh. 

As I suspected it would not logon or attempt to logon to the modem with WPA. I found this fix on the debian site

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

this works and I am currently surfing via the wireless but I have no gui interface to change the ip address without going back to wep (yes it has incited a conflict) and when i do an ifconfig ath0 *address* netmask *address* it then decides not to work again. There is obivoulsy some related file that needs editing, I am missing so any advice on changing the address would be great.

thanks again for the help

---

### Post by bradmayne on 2007-07-19
why do you want to change wifi0 to ath0?  There is no reason for that!

---

### Post by bradmayne on 2007-07-20
dude you don't want to change the wifi0 to ath0.  That's not needed w/ madwifi.  Trust me.  Also you have to have your router broadcasting the SSID also.  I didn't have the router broadcasting SSID and I ran into trouble.  I don't know why your having so much trouble with madwifi.  I had some trouble but not like your having!  I think theres a walkthrough somewhere on the web i'll look in the morning.

---

### Post by aqk on 2007-07-20
Grrr...  Sorry to wake you guys up and re-open this hread, but..
I may be your worst nightmare. 
 I have more or less the SAME problem.

I have done most of this stuff, and still cannot get the ath0 to work.
It 'sees' the router, (ie the essid) but will not  talk to it. 
The eth0 hasno prob- thats what I'm using now.

See  [http://annekowalski.com/2007/06/28/installing-ubuntu-feisty-fawn/feed/](http://annekowalski.com/2007/06/28/installing-ubuntu-feisty-fawn/feed/)  for explanation.

 I'm sorry- it's sad that I can connect Windows Vista effortlessly thru wireless, but I  have to go thru all these command-level machinations to get Ubuntu 7.04 to work...

 Tell me what to do. 
Please don't ask if I have DHCP or DNS on or off; I went thru that s--t years ago.

  I have an ath0 and a wifi0 as network devices.. I followed most of the thread above, but kinda lost it in the terminal commands...
 My mother-in-law would like to 'try wireless', but I guess I am resigned to teaching her Windows...  VISTA!

Lemme know if you wish a ctlC-ctlV  of my  iwconfig or  dhclient etc.. I'll be happy to supply it 

   AND GET RID OF THESE DAMN SILLY SMILIES ON THE RHS of the thread!
(sorry for extreme frustration; I'm all alone on a Friday night and have perchance drunk too much vino..)

---

### Post by amrish on 2007-11-04
I'm having the same problem with the Atheros 5006x, but I can't even connect to unprotected networks as the OP could.

I tried ndiswrapper on the drivers I'm using on my windows XP and they loaded and worked, but unable to connect.
I did " iwconfig " and noticed that sometimes it would alternative between "802.11a" and "802.11g" and sometimes "802.11Tn", even though my network is " 802.11g "

I'm running off the default drivers now and still can't get a connection out. 

With the ndiswrapper drivers I was able to get the dialog to popup that asks for my Network password, but it kept popping up, and then I tried it disabling my network password (it's a WPA/TKIP) and it still wouldn't give me internet access. It'll say it is connected, but there isn't any access to the internet or even the router.

Thanks so much!

---

