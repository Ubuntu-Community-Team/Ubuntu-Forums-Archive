---
title: "Cisco Aironet 350 not connecting (was: New user - New to Linux)"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by manqueller on 2007-02-10
Hello everyone,

     I've been intersted in Linux for a while.  I have so much expierence with windows that I can't help but want something better.  I work at a small company and do server and desktop support.  We are all Microsoft there, but there is one red hat box and I would like to know more about Linux for supporting that computer as well as for switching my home computers to Linux.  

    I have a used sony vaio that I got a good deal on and I've wiped the drive and installed Ubuntu 6.06.  It has a 766Mhz Pentium 3 and 384MB of ram.  It does not have any built in ethernet or wireless.  I was able to get an old PCMCIA 8o2.11b card and when I put it in the lights on the wireless blink as if it's active.  I can even see it on my wireless router but I don't think I'm getting an IP address.  I went to network settings and saw the device and activeated it, but I think I'm missing something.  I'm not even sure how I would check to see if I have an IP or not.  Any help is appreciated. 

I'm really enjoying Ubuntu so far.

Brian

---

### Post by banditti on 2007-02-10
from a terminal window:

ifconfig


Post the results if you have further questions.

---

### Post by rccharles on 2007-02-10
> **manqueller said:**
> Hello everyone,

     I've been intersted in Linux for a while.  I have so much expierence with windows that I can't help but want something better.  I work at a small company and do server and desktop support.  We are all Microsoft there, but there is one red hat box and I would like to know more about Linux for supporting that computer as well as for switching my home computers to Linux.  

    I have a used sony vaio that I got a good deal on and I've wiped the drive and installed Ubuntu 6.06.  It has a 766Mhz Pentium 3 and 384MB of ram.  It does not have any built in ethernet or wireless.  I was able to get an old PCMCIA 8o2.11b card and when I put it in the lights on the wireless blink as if it's active.  I can even see it on my wireless router but I don't think I'm getting an IP address.  I went to network settings and saw the device and activeated it, but I think I'm missing something.  I'm not even sure how I would check to see if I have an IP or not.  Any help is appreciated. 

I'm really enjoying Ubuntu so far.

Brian

I'll add a few more works...

applications > accessories > terminal

ifconfig

You can put the output of ifconfig to a file by typing

ifconfig >seeifconfig

cat seeifconfig

The file is ~/seeifconfig

You can put the file on your desktop by:
cd Desktop
ifconfig >seeifconfig

cat seeifconfig


You may copy seeifconfig to a memory stick or floppy. Look under the places menu for the home folder. 

...

You might try the ping command:

ping -c4 [www.linux.org](www.linux.org)
ping  -c4 198.182.196.56


You could try pinging your router too.

............

You might try a modem connection if you have a modem.  External modems are better. It's good to have some internet connection because the Ubuntu software is all downloaded.

..........

You might want to get a book on Ubuntu.  There arriving in public libraries.

Robert

---

### Post by nickoli_02 on 2007-02-10
If you haven't done so already you'll need to configure your wireless settings with your SSID and password. The default security for ubuntu is WEP, if you want to use WPA you'll have to do some more configuration. Try searching the forums for wpa_supplicant if you want a howto on it. 

To configure your wireless go to System -> Administration -> Networking, select your wireless connection and click "properties". It should be pretty self explanatory from there :)

---

### Post by manqueller on 2007-02-12
Thanks!  I probably should have mentioned that, but right now I don't have any WEP or WPA on my wireless router.  I just use a MAC filter, and I've already put the MAC for the wireless card on the list.

---

### Post by manqueller on 2007-02-13
Ok here's what I've found.  If I go to Network tools there are three network interfaces:
loopback interface (l0)
ethernet interface (eth0)
unknown interface (wifi0)
the configure button next to all of them is greyed out.  The laptop has no ethernet jack anywhere, just the PCMCIA wireless card I put in.  If I remove the PCICIA wireless card and go back to network tools I only see the loopback interface.  

If I go to networking  I see the ethernet inteface and a wifi interface and both are enabled.  There I also see the modem.  Again if I remove the PCMCIA card only the modem is there.  

In Device manger I see a 350 Series Wireless LAN adapter, but the manufacturer, etc all say Unknown.  The actual device I've used is a Cisco Aironet 350.

---

### Post by igknighted on 2007-02-13
Try downloading the .deb package for a program called wifiradar (or there is another one that is good as well, I can't remember its name) and installing it via a usb stick.  This program lets the computer scan for wireless networks within range and connect to them similar to the way winXP does (without the annoying wizards)

---

### Post by Brunellus on 2007-02-13
> **manqueller said:**
> Ok here's what I've found.  If I go to Network tools there are three network interfaces:
loopback interface (l0)
ethernet interface (eth0)
unknown interface (wifi0)
the configure button next to all of them is greyed out.  The laptop has no ethernet jack anywhere, just the PCMCIA wireless card I put in.  If I remove the PCICIA wireless card and go back to network tools I only see the loopback interface.  

If I go to networking  I see the ethernet inteface and a wifi interface and both are enabled.  There I also see the modem.  Again if I remove the PCMCIA card only the modem is there.  

In Device manger I see a 350 Series Wireless LAN adapter, but the manufacturer, etc all say Unknown.  The actual device I've used is a Cisco Aironet 350.
I'm editing the thread title to reflect the nature of the help request.  please post a succinct summary of your problem--that way those who can help you know that they can do so.

First, we need some more specific information about your hardware and what, exactly, is going on.

I gather that the computer in question has no 'net connectivity at all.  Do you think you'd be able to transfer some log files to a computer with net connectivty? if you could, we could get a very good idea of what exactly is going on...

---

### Post by Crooksey on 2007-02-13
Erm, idk why you are all giving ifconfig commands.


Open a terminal then type
```

iwconfig 


```

This will return something like
```

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Now take note to the device name, now in a terminal type...

```

gedit wireless            <-- this command will open a new text input window, in that window type

iwconfig eth1 essid "youressid"
iwconfig eth1 key YOURKEYHERE
dhclient eth1

<-- save the program, close the window

chmod +x wireless
./wireless

```

Make sure to change device names accordingly.

---

### Post by Brunellus on 2007-02-13
> **Crooksey said:**
> Erm, idk why you are all giving ifconfig commands.


Open a terminal then type
```

iwconfig 


```

This will return something like
```

eth1      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Now take note to the device name, now in a terminal type...

```

gedit wireless            <-- this command will open a new text input window, in that window type

iwconfig eth1 essid "youressid"
iwconfig eth1 key YOURKEYHERE
dhclient eth1

<-- save the program, close the window

chmod +x wireless
./wireless

```

Make sure to change device names accordingly.
because OP's problem is not about associating to the access point, apparently, but successfuly getting an IP via DHCP from the router.  

I suspect that OP is suffering from [Bug #62685 ](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62685/) but would like to confirm by seeing the relevant logs.

---

### Post by manqueller on 2007-02-18
Thanks for all the help with this.  When I type IWconfig I get 

eth0:  and I get a wifi0 and they both give the same information.  It does see the ESSID of my wireless but for access Point: it says invalid.  I'm not sure what to make of that.  

I typed gedit wirelsss and input the information and saved the program.  I double checked my router and I do have the correct MAC address entered in the MAC filter of the router.  I also tried disabling the MAC filter, but still I get invalid for the access point when I type in iwconfig.  

if I type ifconfig it looks like I have an IPv6 address.

---

### Post by manqueller on 2007-03-05
What logs do you want to see?

---

### Post by mootpoint on 2007-03-06
manqueller: I have the same network card. For whatever reason, the dhcp client doesn't run when it connects to a network. I've had various other difficulties with the GUI tools as well, including hitting a bug that was crashing the network admin tools.

Try this command first at a terminal; it'll probably fix your problem:

sudo dhclient eth1

If that doesn't fix it, try the following series:

sudo iwconfig wifi0 essid SSIDOFOPENNETWORK

sudo ifconfig -s eth1 add <192.168.1.123/24>             
****OR****
sudo dhclient eth1

sudo ifconfig -s eth1 mtu 1392 ****Only if you are using PPPOE for your internet connection*****

sudo route add default 192.168.1.1

HTH,
m00t

---

### Post by manqueller on 2007-03-08
Thanks for the help with this, the first command worked and I got connected to my router.  Now I've got 222 updates to install :-)  

If anyone's interested I found a company that sells machines with Ubuntu pre-installed and they have free 'Powered by Ubuntu' stickers.  I put one on my laptop.

[http://system76.com/index.php/cPath/53_64](http://system76.com/index.php/cPath/53_64)

---

