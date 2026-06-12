---
title: "can't connect to internet!"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by futonwrath on 2007-01-06
Hey, I just installed ubuntu 6.10 on a pentium III, so I just did the command line installation. I am trying to get the internet to work from the command line. I use a cable modem that plugs into an ethernet card. Ubuntu is detecting the card fine. I was just wondering how to get the internet to work (from the command line). Thanks for the help.

---

### Post by riven0 on 2007-01-06
:confused: Should have been detected automatically. Can you try this and post the output?:

> sudo /etc/init.d/networking restart

Then try pinging just to be sure:

> ping google.com 

---

### Post by futonwrath on 2007-01-06
"reconfiguring network interfaces... ok"

unknown host google.com

I am unplugging the cable from this computer and plugging it into the ubuntu one each time I try something... but I gave it a little time before I typed those commands.

---

### Post by Famicommie on 2007-01-06
At the command line try:

```
dhclient
```

---

### Post by futonwrath on 2007-01-06
No DHCP offers received.
This was after some output from something called DHCPDISCOVER, trying to connect to 255.255.255.255.

Could my internet provider use some kind of username/password setup or something? I have comcast cable internet. But it seems like it wouldn't need verification, since it keeps working fine when I am unplugging it and plugging it back in to this Windows machine.

---

### Post by quartzy on 2007-01-06
Usually if you are connecting via a ethernet port you arn't in control of what the router does so it has nothing to do with your ISP, what sort of router do you have? And did you have to setup your modem (ie login to it with a web browser?)

---

### Post by futonwrath on 2007-01-06
I don't have a router... just a cable modem with one ethernet cable.

---

### Post by futonwrath on 2007-01-06
I don't have to login to the modem, as far as I can tell.

---

### Post by quartzy on 2007-01-06
cable modem model number? (should be writtern on it somewhere)

---

### Post by futonwrath on 2007-01-06
Scientific Atlanta DPC 2100 Series

Hey, thanks for the help, by the way... :)

---

### Post by quartzy on 2007-01-06
Very weird that it's not working..  Can you post the entire output of the command riven0 asked you to do?

```
sudo /etc/init.d/networking restart
```

EDIT: Also could you post the contents of /etc/network/interfaces please?

---

### Post by futonwrath on 2007-01-06
sudo /etc/init.d/networking restart:
* Reconfiguring network interfaces... [ok]



dhclient:

There is already a pid file /var/run/dhclient.pid with pid 6648
killed old client process, removed pid file.

Listening on lpf/eth0/00:10:b5:d6:cc:d7
Sending on lpf/eth0/00:10:b5:d6:cc:d7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received
No working leases in persistent database - sleeping.

---

### Post by quartzy on 2007-01-06
> **quartzy said:**
> EDIT: Also could you post the contents of /etc/network/interfaces please? 

:)

Also have you tried restarting the modem?

---

