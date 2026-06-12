---
title: "Terminal equivalent"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-01
Hey,

When I log into Ubuntu, to get onto the wireless network in my home, I got to:
system > administration > networking
I click on the wireless internet (ra0), make it use the DHCP instead of a static IP, click on 'Ok', then enable the connection. Once enabled, I click on it again to select the network name (linksys).

What I want to know is, how would I do this exact same thing, in the terminal?

Thanks, 

Jimmey

---

### Post by marks_linux on 2006-01-01
Me thinks you can do it by editing /etc/network/interfaces

against the network device you can specify static or otherwise. If you look at that file know it probably has the setting for the setup you have just done.

---

### Post by Jimmey on 2006-01-01
I looked there, but didn't see anything interesting, and I saw nothing regarding ra0. :S

Edit:

Basically, how would I enable the interface ra0 through the terminal?

---

### Post by lunatech on 2006-01-01
[QUOTE=Jimmey]
Edit:

Basically, how would I enable the interface ra0 through the terminal?[/QUOTE]

If the ra0 interface is configured, then from the xterm do - 'sudo /sbin/ifup ra0'
That will bring ra0 up

---

### Post by Jimmey on 2006-01-01
Yeah, I've been playing with ifup, but...
It only works once I enable the ra0 in the GUI.
If I don't, it says
> Ignoring unknown interface ra0=ra0.
So, how to enable it?

---

### Post by cwaldbieser on 2006-01-01
[QUOTE=Jimmey]Yeah, I've been playing with ifup, but...
It only works once I enable the ra0 in the GUI.
If I don't, it says

So, how to enable it?[/QUOTE]
If you type "ifconfig", is "ra0" one of the interfaces listed?  If not, what about "iwconfig" (since it's wireless)?

You should be able to set it to use DHCP by using the "dhclient" command, but if you need to scan for an access point, there are various iw* commands (like "iwlist").

---

### Post by Jimmey on 2006-01-01
Yeah, ra0's there, and I can get it working, I just wondered how I would do that without the GUI..

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=Jimmey]Yeah, ra0's there, and I can get it working, I just wondered how I would do that without the GUI..[/QUOTE]
I think you use "iwconfig" to configure the network name, and then "dhclient" to dynamically fetch the IP address.
```

$ sudo iwconfig ra0 network-name
$ sudo dhclient ra0

```
I could be off a little on the wireless syntax.  Check out the man pages for iwconfig.

---

