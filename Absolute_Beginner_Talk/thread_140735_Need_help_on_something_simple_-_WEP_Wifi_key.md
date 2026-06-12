---
title: "Need help on something simple - WEP Wifi key"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by n1tro on 2006-03-06
Hello,

I am trying to enter the wep key for my wifi to work on my laptop. The wifi is working if I hijack the neighbor's unsecure Internet connection but when I go to put in the key for my own connection it doesn't work. My key is 1111111111 <--- sad I know but thats what I am using. When I go to the properties to enter in the key, it gives me 2 options. ie. either Ansi or Hexidecimal. I enter my key in bother and it doesn't work. I convert my 1111111111 to hexidecimal which apparently is 423a35c7 and that still doesn't work. Please help a noob out and point out the obvious thing that I am doing wrong. Thanks.

PS. Yes my key works when I am under Windows XP

---

### Post by mdsmedia on 2006-03-06
This might help. I'm new to WEP myself, but are you entering the 1111.... key as ansi or Hex?

If you're entering it as ansi, try entering it as a Hex key.

---

### Post by paulmilliken on 2006-03-06
WEP keys are normally hexadecimal and 1111111111 is a valid hexadecimal number so that should work.  I suggest trying a static IP address and entering the netmask and gateway address manually to simplify the process and hopefully track down the problem.  The netmask and gateway addresses should be in the documentation for your wireless access point.

---

### Post by jjf on 2006-03-06
Maybe you're having more luck than I, but in my experience wifi is not "something simple."  :mad: 

I've got mine working at home but not at work.  I need to use ndiswrapper because my card isn't natively supported in Ubuntu, so maybe your process is simpler.  Here are some of the links I've been using:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

Anyway, what I've had to do is edit the file /etc/network/interfaces

In a terminal:
> sudo cp /etc/network/interfaces /etc/network/interfaces_bak
sudo gedit /etc/network/interfaces

My configuration looks like this:

> 
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0
	map eth0

# added manually on 3/5/2006
iface wlan0 inet dhcp
wireless_keymode open
wireless_mode managed
wireless_nick XXXXX *(your router's hostname, if any)*
wireless-essid XXXX *(your SSID)*
wireless-key 1111111 *(your WEP key in hexadecimal. if you want to put it in ASCII, put a "s:" before it like this: **wireless-key s:1111111**)*

auto wlan0

iface eth0 inet dhcp


Good luck.

---

### Post by n1tro on 2006-03-06
Ok, I tried everything that was posted and still no luck. I think this problem has something to do with the fact that I am using the ndiswrapper and/or Broadcom based wifi and possibly Ubuntu 5.10. Reason I say this is because in my previous laptop, I had the Intel 2200 B/G wireless and it was detected fine in Ubuntu 5.04 and I just entered in the same key and it worked. Oh well, got to keep "borrowing" neighbor's unsecure wifi for now until some else has any other ideas.

---

### Post by paulmilliken on 2006-03-06
[QUOTE=n1tro]Ok, I tried everything that was posted and still no luck. I think this problem has something to do with the fact that I am using the ndiswrapper and/or Broadcom based wifi ...[/QUOTE]
N1tro,
I don't think it has anything to do with ndiswrapper because you're picking up your neighbour's LAN without any trouble.  Sometimes it takes a while for the wireless access point to get up-and-running so try leaving it for a few minutes and trying again.  Also, check that your essid is correct.
Paul

---

### Post by n1tro on 2006-03-06
You're right. Must be something buggy with my setup or Ubuntu. I know the SSID is correct because when Ubuntu is loaded up, it sees both my wifi (USR8054) and the neighbors' (Linksys). The problem starts when I pick the USR8054 and enter in 1111111111 in either ANSI or HEX. Just no connection no matter how long I leave it.

---

