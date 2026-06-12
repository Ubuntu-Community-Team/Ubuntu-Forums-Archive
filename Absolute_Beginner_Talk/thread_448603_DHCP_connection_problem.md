---
title: "DHCP connection problem"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Screwtape on 2007-05-19
Hi-
I am having trouble getting my ethernet connection to work on my newly-ubuntu-converted laptop. The laptop is a Compaq Presario from last year, and Ubuntu 7.04 Feisty Fawn seems to know that the card is there (when I plug the LAN cable into the jack, it recognizes it and claims to be connected). Unfortunately, when I start Firefox, it can't find the internet. I have two ethernet cards; the one I'm trying to use, which Ubuntu calls eth0, and my wireless card, which it calls eth1. In the system log, the messages for eth0 all read "link up, 100Mbps, full-duplex, lpa 0x45E1."

I apologize if I've left out any relevant details; I am very new at this. Any help would be greatly appreciated.
-s.

---

### Post by Metacarpal on 2007-05-19
How does your computer connect to the internet?  Is it on a LAN, connected directly to a cable/DSL modem, or plugged into a router or switch that is connected to the cable/DSL modem?  Or is it something else entirely?

It could be a matter of firewall or proxy settings if you're on a network.

Also, for a little extra info, open a terminal (Applications menu > Accessories > Terminal) and type in:
```
ifconfig
```
and copy/paste the output here.

---

### Post by Screwtape on 2007-05-19
Sorry; the computer connects directly the cable modem box via ethernet cable.

---

### Post by jimrz on 2007-05-19
> **Screwtape said:**
> Sorry; the computer connects directly the cable modem box via ethernet cable.

have you added the correct DNS settings for you ISP and whatever else they may require to your network settings?

---

### Post by Screwtape on 2007-05-19
> **jimrz said:**
> have you added the correct DNS settings for you ISP and whatever else they may require to your network settings?

could you tell me how to do that? I don't require a password to log on or anything, but I don't know how to fix the DNS settings.

---

### Post by Bachstelze on 2007-05-19
YOur DNS settings are stored in /etc/resolv.conf. Do this

```
sudo nano -w /etc/resolv.conf
```

and edit to your needs.

---

### Post by Screwtape on 2007-05-19
The thing is, I don't have preassigned DNS settings; I just plug the ethernet cable into the back of the computer and DHCP assigns the address.

Ubuntu has the little computer icon up in the corner that shows that the ethernet cable is connected - it runs the little balls chasing each other in a circle, and then it seems to resolve and know that the ethernet connection is there.

---

### Post by Bachstelze on 2007-05-19
Then all you need is to connect with DHCP ? Just run

```
sudo dhclient eth0
```

---

### Post by Screwtape on 2007-05-20
> **HymnToLife said:**
> Then all you need is to connect with DHCP ? Just run

```
sudo dhclient eth0
```

Well, that has definitely done something new - now the browser searches for the web page, rather than acting like it's offline. Unfortunately, it times out every time it tries.

---

### Post by Bachstelze on 2007-05-20
Have you tried to ping a website to see if it works ?

---

### Post by Screwtape on 2007-05-20
No; I'm afraid I think the problem is elsewhere. The computer is telling me that it's not getting any DHCPOFFERS or something like that, and it's also identifying a third wireless device called eth0:avah. When I do sudo dhclient eth0:avah, it says "cannot assign requested address" and then a couple of lines later, "no such device."

---

### Post by wormser on 2007-05-20
> **Screwtape said:**
> Sorry; the computer connects directly the cable modem box via ethernet cable.

I have seen a few posts with the same issue of plugging directly into a cable modem.  There must be a bug.  One guy said his Feisty upgrade from Edgy worked and his clean install of Feisty did not work unless he manually does sudo dhclient after each boot.  Maybe something changed between Edgy and Feisty with DHCP?  I am going to test plugging directly into a cable modem tomorrow.

On another note.  You should get a router instead of plugging directly into the modem.  It provides extra security and allows multiple computers to connect.

---

### Post by Screwtape on 2007-05-20
Yeah, I have a router but it is extremely fickle. This will probably give me incentive to fix it...

---

