---
title: "wlan1:avahi has taken over my wireless!"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-10-15
Okay, I followed [this]("http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73") guide to get my D-link USB adapter working on Ubuntu 7.04.

For quite a while it worked. It was great.

And then suddenly for no reason it disconnected.  But now, when I type

```

ifconfig -a

```

I get wlan1, and wlan1:avahi, and only wlan1:avahi is active.  Before, when I set it up, it was only wlan0, and it was fine.

Somebody who knows a bit about wireless in ubuntu, please help me. I've googled this, several other people have the same problem, but no solution was actually mentioned. All I know is I need to get it to use wlan1 instead.

Yeah, I'm using the RT73 module and the card ID is for dwl-g122 rev. c1

It is a USB wireless.

Thanks for any help you can give.

---

### Post by wormser on 2007-10-15
I am not an expert on this but I believe this will do the trick.  You need to turn off avahi.  System> Administration> Network> General tab> Uncheck Automatic Service Discovery. Try restarting your networking service.  sudo /etc/init.d/networking restart.  If that does not work then reboot.  Post your results.

---

### Post by Neon_Knight on 2007-10-15
> **wormser said:**
> I am not an expert on this but I believe this will do the trick.  You need to turn off avahi.  System> Administration> Network> General tab> Uncheck Automatic Service Discovery. Try restarting your networking service.  sudo /etc/init.d/networking restart.  If that does not work then reboot.  Post your results.

Thank you.  I have tried that, to no avail.

```

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan1.pid with pid 4927
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:1b:11:15:a6:01
Sending on   LPF/wlan1/00:1b:11:15:a6:01
Sending on   Socket/fallback
DHCPRELEASE on wlan1 to 192.168.2.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Network is down.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan1 ; Network is down.
There is already a pid file /var/run/dhclient.wlan1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:1b:11:15:a6:01
Sending on   LPF/wlan1/00:1b:11:15:a6:01
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


```

What do you make of it?

---

### Post by wormser on 2007-10-15
That code looks like DHCP is failing to give you an IP address.  Did you reboot you computer after making the earlier sugestion?  Post the results of:

```
less /etc/default/avahi-daemon
```

If Avahi is off it should look like this:

> # 0 = don't start, 1 = start
AVAHI_DAEMON_START=0

Turning Avahi off should get rid of wlan1:avahi.

---

### Post by Neon_Knight on 2007-10-15
Right, well 
```

less /etc/default.avahi-daemon

```
comes up with
```

# 0 = don't start, 1 = start
AVAHI_DAEMON_START=0

```

But wlan1:avahi still comes up on the ipconfig.

---

### Post by wormser on 2007-10-15
Did you restart the computer?

---

### Post by Neon_Knight on 2007-10-15
Some more info that might help.

I try to connect with:

```

   
       sudo ifconfig wlan1 up

       sudo iwconfig wlan1 essid YOUR_NETWORK_NAME_HERE

       sudo iwconfig wlan1 key YOUR_WEP_KEY_HERE

       sudo dhclient wlan1 
      

```
(replacing YOUR_NETWORK_NAME_HERE and YOUR_WEP_KEY_HERE with the right things)

It tells me

```

unrecognised wireless request

```

---

### Post by Neon_Knight on 2007-10-15
> **wormser said:**
> Did you restart the computer?

Yes.

---

### Post by Keith_Burton on 2007-10-15
I had trouble getting my wireless to work under Feisty, and was told to comment out the lines in /etc/network/interfaces (add a "#" at the beginning of each line) that deal with the wireless adapter. Let the GUI network manager handle configuring and activating the wireless.

It worked for me, but I'm using a PCMCIA adapter instead of USB, and on Kubuntu. KDE may be different than Gnome in this.

But if you backup the interfaces file first, it can't hurt and doesn't take long to try.

---

### Post by Neon_Knight on 2007-10-15
Ok. I turned the router off, then turned it back on and it looked as though the wireless was working, both lights were flashing. When I tried 

```
sudo ifconfig wlan1 up

sudo iwconfig wlan1 essid YOUR_NETWORK_NAME_HERE

sudo iwconfig wlan1 key YOUR_WEP_KEY_HERE

sudo dhclient wlan1
```

it came up with

```
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:1b:11:15:a6:01
Sending on   LPF/wlan1/00:1b:11:15:a6:01
Sending on   Socket/fallback
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPNAK from 10.0.0.138
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.2.1
DHCPREQUEST on wlan1 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.2 -- renewal in 954993185 seconds.
```

and still no internet. I've tried restarting, and it does the same. Avahi seems to be gone, and in Network Tools it says wlan1 is active, and yet it isn't working..

---

### Post by wormser on 2007-10-15
Do you have a valid ip address in ifconfig?  Have you tried pinging the router, a web site and the ip address of that site?  Try connecting with the network tool next to the clock.  Also, try connecting with no encryption.

---

### Post by Neon_Knight on 2007-10-16
> **wormser said:**
>  Try connecting with the network tool next to the clock

You mean gnome network manager? That guide said I had to uninstall gnome network manager for it to work properly.  The other stuff you said, I'll try in a minute.

---

