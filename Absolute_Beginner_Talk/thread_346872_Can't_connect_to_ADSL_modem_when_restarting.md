---
title: "Can't connect to ADSL modem when restarting"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by gyalakias on 2007-01-26
OK, this is seriously not an issue that is very serious, but it's annoying more than anything else. Whenever I shut down or restart the computer, I can't connect to the internet. So I try connect to the router and I get a "Server Busy" signal.

I go to the terminal and I type:

```

sudo dhclient eth0

```

And I get this message:
```

Listening on LPF/eth0/00:0e:0c:5a:c1:5e
Sending on   LPF/eth0/00:0e:0c:5a:c1:5e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
SIOCADDRT: Network is unreachable
bound to 85.75.244.127 -- renewal in 1268862 seconds.

```

Two questions:
A)What the $%^ is going on?
B)How do I fix this?

The problem gets fixed once I reset the modem and restart the computer, but seriously it gets annoying having to do that every single time I want to get on the net.

Thanks in advance

---

### Post by r4ik on 2007-01-26
Uncomment and edit (as root, ie sudo nano) the PREPEND line of /etc/dhcp3/dhclient.conf and place your isp's dns nameserver(s) there. In the case of multiple nameservers, be sure to separate them with a comma, and end the line with a semicolon;
Save the file.
After that reboot.

---

### Post by gyalakias on 2007-01-26
OK, the prepend line is like this:

```

#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;

```

And the name servers I have are:

otenet.gr nameserver = ns2.otenet.gr
otenet.gr nameserver = ns1.otenet.gr
ns2.otenet.gr internet address = 195.170.2.1
ns1.otenet.gr internet address = 195.170.0.2

What is the new code going to be like?

Sorry for asking for the code directly but I don't want to mess up my modem.

---

### Post by r4ik on 2007-01-26
Sorry i am late please remove 127.0.0.1;

and replace with

195.170.2.1,195.170.0.2;

exactly as is.
save the file and reboot.

---

### Post by gyalakias on 2007-01-27
Nope, didn't work... and my X Server crashed....

It's weird but the problem was not there in version 6.10 of Xubuntu, it is present only in Dapper Drake.

---

### Post by r4ik on 2007-01-27
You're xserver crashed on a dhcp change? 
Strange.
Would you change you're dns in networksettings please ?
Just remove the first entry prob. 127.0.0.1;
and replace them with the numbers you put in you're prepend line.
You could also add lan to you're search domains.
Also check the prepend line to make sure the # in front is out.
Check the numbers and reboot agian.If that does not work i am out of ammo.

Good luck !

---

