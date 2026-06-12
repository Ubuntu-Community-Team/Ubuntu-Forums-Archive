---
title: "wireless and wired ip addresses, and unable to share home directory"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Tim from Tang on 2007-02-17
HI All,
I have been using ubuntu on my desktop for some time (and other dists before that) I am new however to the world of broadband and networking, having only just got a broadband connection, and a thinkpad t40 laptop.

I have a couple of questions,
First I notice that my router assigns different ip addresses to my wired and wireless connections on the lappy, the laptop is running ubuntu 6.10. Is this normal or correct? With the wired connection plugged in I get a different ip for the wired and wireless connections.

I have been fumbling around with samba to try and share files between my desktop (ubuntu 6.06, and fixed ip from router) and laptop. I can share my music folder fine (the music folder resides in the home folder on the desktop and is accessible to all users on the desktop) If I open network places on the laptop I can navigate to the music folder and open and play files. I can also share files or folders from the laptop home directory with the desktop ( I have shared the examples folder from the install to try this out ) and I can open files on the desktop fine. However I have tried to share files from my home directory on the desktop with the laptop and I can see the shared folder in network places, but can't open it? I wonder what might be going on?

Note that fumbling around is a good description, I am new to networking. I will post the contents of relevand configuration files If somebody asks for the files by name, I do not know which ones might be relevant.

---

### Post by dbott67 on 2007-02-17
> First I notice that my router assigns different ip addresses to my wired and wireless connections on the lappy, the laptop is running ubuntu 6.10. Is this normal or correct? With the wired connection plugged in I get a different ip for the wired and wireless connections.

Yes, this is the correct behaviour.  You should only be using one interface (either wired or wireless) at a time, unless you're configuring the computer as a router/firewall/NAT device.

Each network card can function independently of the other network card, which is the basic premise of a network router.  Interface A has an IP address on the internal network, while interface B has an IP on the external network.  If a packet of information reaches the router that has an address that does not exist on the internal LAN, the router would forward the packet to the external interface, which would, in turn, forward the packet to the next router until it reaches it's ultimate destination.

Having 2 functioning NICs on the same network can lead to some problems unless you have some additional software, such as nic-teaming (aka fault tolerance in the event that the primary NIC fails).  Even with NIC teaming, both NICs get assigned the same IP address.  In your case, your NICs are getting different IPs on the same network, which can make it difficult for name resolution when other devices try to connect over the network.

As for Samba, you can take a look here for tips on configuration, etc. and perhaps take a look at the package 'swat'.

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html)

-Dave

---

### Post by Tim from Tang on 2007-02-17
Thanks for your prompt reply. Leaving aside the Samba issue for the moment ( I think it is something to do with the access control to my home directory on the desktop). So If I understand you correctly I should have only one of the three available networking interfaces on my Thinkpad T40 active at any one time. i.e. either the wired connection, or one of the two wireless interfaces? Is there any way that I can set up the machine to do this for me automatically, or do I need to activate the wireless interface and deactivate the wired interface through the networking dialog each time I go walkabout?

All the Best
Tim from Tang

---

### Post by dbott67 on 2007-02-17
Correct --- just use one interface at a time.

I'm not aware of any 'automatic' way to disable/enable a specific interface.  Other than using the GUI Network application to activate/deactivate, you could issue the following commands from the terminal:
```
sudo ifdown <interface>
```

Replace <interface> with the appropriate interface (eth0, eth1, eth2, wlan0, ath0, etc).  So to disable eth0 (probably your wired interface), you would issue the command:

```
sudo ifdown eth0
```

To activate it, you would use:
```
sudo ifup eth0
```

Repeat for the other interfaces that you wish to disable/enable.

If this seems somewhat cumbersome, you could write a little script to disable/enable each one of your NICs:

**_SCRIPT TO DISABLE NIC_**

1. Create a new script file:
```
gedit ~/Desktop/disable_[COLOR="Red"]eth0[/COLOR].sh
```

2. Paste in the following text:
```
#!/bin/bash
sudo ifdown [COLOR="Red"]eth0[/COLOR]
```

3. Save & exit.

4. Set file executable:
```
chmod a+x ~/Desktop/disable_[COLOR="Red"]eth0[/COLOR].sh
```

5. Double-click to execute.

6. Repeat for other interfaces as desired, replacing **[COLOR="Red"]eth0[/COLOR]** with appropriate interface.

**_SCRIPT TO ENABLE NIC_**

1. Create a new script file:
```
gedit ~/Desktop/enable_[COLOR="Red"]eth0[/COLOR].sh
```

2. Paste in the following text:
```
#!/bin/bash
sudo ifup [COLOR="Red"]eth0[/COLOR]
```

3. Save & exit.

4. Set file executable:
```
chmod a+x ~/Desktop/enable_[COLOR="Red"]eth0[/COLOR].sh
```

5. Double-click to execute.

6. Repeat for other interfaces as desired, replacing **[COLOR="Red"]eth0[/COLOR]** with appropriate interface.

-Dave

---

### Post by Tim from Tang on 2007-02-17
Many Thanks this is really helpful. I will write the scripts so that I can click to activate and deactivate my interfaces. I have not had the laptop out and about yet, but when I do, should it simply connect to wireless hotspots etc when present, or is there some standard way to configure the wireless interfaces to connect to wireless hotspots in hotels coffee shops etc.

All the best
Tim from Tang

---

### Post by dbott67 on 2007-02-17
For wireless, there are a few GUI utilities available in the repositories:

Network Manager
```
sudo apt-get install network-manager-gnome
```

Wifi-Radar
```
sudo apt-get install wifi-radar
```

You can read up on them here:

[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)
[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)


**_Command Line_**

If you're more comforatble at the command line:
```
iwlist scanning
```

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID</size:small?:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

After locating a hotspot using **iwlist scanning**, you then need to configure the ESSID & WEP key (if applicable) using **iwconfig** (check **man iwconfig** for usage).

-Dave

---

