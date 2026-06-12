---
title: "Changing MTU"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by MarkX on 2008-01-30
I have just installed Ubuntu on (also beginner) friend's computers. Their broadband connection is pretty bad so I have to tweak it to the best of my limited abilities. Their ISP requires (nay demands!) an MTU of 1400.

A SIMPLE WAY OF SETTING THE MTU IN UBUNTU PLEASE.

---

### Post by Joeb454 on 2008-01-30
Surely it should be the ISP who tells you how to do this. If they require it, they should also provide instructions on how to do it with various modems/routers.

I know I have no clue at all how to change the MTU in Ubuntu or any other OS for that matter

---

### Post by Golem XIV on 2008-01-30
Try [this link]("http://ubuntuforums.org/archive/index.php/t-82093.html")
or a bit more detailed [here]("http://www.debianadmin.com/tag/change-mtu-ubuntu/")

---

### Post by njparton on 2008-01-30
Edit /etc/networking/interfaces.conf

and put in the following line in the section that relates to your nic (eth0?).

mtu 1400

Reboot or restart networking.

That's it.

---

### Post by MarkX on 2008-01-30
> **Joeb454 said:**
> Surely it should be the ISP who tells you how to do this. If they require it, they should also provide instructions on how to do it with various modems/routers.

I know I have no clue at all how to change the MTU in Ubuntu or any other OS for that matter

They do give instructions for routers and windows but not for the numerous distributions of Linux. I can't find a "how to" for it anywhere.

---

### Post by MarkX on 2008-01-30
I'll try the above suggestions later, many thanks.

---

### Post by MarkX on 2008-02-01
Can't find " /etc/networking/interfaces.conf". 

Having real problems with firefox too. It won't connect to google at all (or hotmail post-login). Most other sites load fine and it all works with XP.

---

### Post by jan quark on 2008-02-01
try this

```
sudo gedit /etc/network/interfaces
```

---

### Post by MarkX on 2008-02-01
> **jan quark said:**
> try this

```
sudo gedit /etc/network/interfaces
```

Did that and it just says:

auto lo
iface lo inet loopback

When I do 
sudo gedit /etc/network/interfaces.conf

it just comes back with an empty file.

---

### Post by jan quark on 2008-02-01
this will change the mtu 

```
sudo ifconfig eth0 mtu 1400
```

note: change eth0 to your network device
you can find that by doing a scan

```
sudo iwlist scan
```

to make the change permanemt
type

 mtu 1400

 into the interfaces file

then do the following
```
sudo ifdown eth0
``` < change eth0 accordingly to your device name
```
sudo ifup eth0
```
```
ifconfig
```

---

### Post by njparton on 2008-02-01
You don't appear to have a valid network connection in your interfaces file so you'll need to rectify that first.

It should be listed as eth0 or eth1 etc...

Only then can you make a permanent change to the mtu.

---

### Post by MarkX on 2008-02-01
> **njparton said:**
> You don't appear to have a valid network connection in your interfaces file so you'll need to rectify that first.

It should be listed as eth0 or eth1 etc...

Only then can you make a permanent change to the mtu.

There is nothing there, it's a blank page but internet mostly  works.
Firefox does get most sites including update and repos  but refuses to load google and Hotmail.

---

### Post by MarkX on 2008-02-01
> **jan quark said:**
> this will change the mtu 

```
sudo ifconfig eth0 mtu 1400
```

note: change eth0 to your network device
you can find that by doing a scan

```
sudo iwlist scan
```

to make the change permanemt
type

 mtu 1400

 into the interfaces file

then do the following
```
sudo ifdown eth0
``` < change eth0 accordingly to your device name
```
sudo ifup eth0
```
```
ifconfig
```

How do I change eth0 to be my default network device? I thought it already was, since I can get onto the net (via my wired router).

---

### Post by njparton on 2008-02-01
"lo" is just the local loopback so I'm not sure how you're managing to connect to the internet without an "eth0" entry in there.

Are you connecting via USB rather than ethernet?

If so maybe you won't get an entry in this file in which case I don't think you can change your mtu as this isn't relevant to a pc to modem connection via usb.

---

### Post by MarkX on 2008-02-01
> **njparton said:**
> "lo" is just the local loopback so I'm not sure how you're managing to connect to the internet without an "eth0" entry in there.

Are you connecting via USB rather than ethernet?

If so maybe you won't get an entry in this file in which case I don't think you can change your mtu as this isn't relevant to a pc to modem connection via usb.

No, it's via  Lan.
 I think I'll completely reinstall ubuntu, once I figure out how to do it without wiping other partitions and grub getting messed up. If that doesn't work I'll have to put my friends back on XP alone. I can't fiddle around at their place for hours.

---

