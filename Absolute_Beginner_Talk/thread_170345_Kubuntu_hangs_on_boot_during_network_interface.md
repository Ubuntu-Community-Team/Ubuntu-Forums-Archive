---
title: "Kubuntu hangs on boot during network interface"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by n3tfury on 2006-05-04
Hi folks.  I was hoping to not have to ever post a topic because there is so much good information to be had here, but I'm not having too much luck finding an answer for this one:

I'm using Dapper Beta2 (because it works with my Airlink card) and am pleased that I can now be untethered, but now I have a problem after I tried to configure WEP (WPA looks like a real pain in the @ss).

After configuration, the system hung, so I had to hard boot. Now, in both normal and recovery mode, the boot hangs during "Configuring network interfaces".  Obviously, if I remove the card, all is well and I can boot into the system.

I'm thinking that I need to edit my etc/network/xxxxx file back to default.  I'm on windows right now and don't recall the exact name, but it holds the essid, WEP, and other pertinent info.  

What does the default file look like? Or can I just delete this file and upon boot, it creates another default configuration?

Thanks for any help.

---

### Post by n3tfury on 2006-05-04
woot!  I got brave and edited the file (interfaces) and commented out the essid, wep, etc that were altered.   I'm sitting on an open network, but at least I can boot and access the network.

if someone could still post what this file looks like by default, I would appreciate it!

---

### Post by MartinJ on 2006-05-04
This is NOT the default interfaces file.  I used to have the same problem with the hanging startup.  After lots of messing about I got it to work with the following:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid wirelessnamehere
	wireless-key1 9014247342

```

Hope that helps!

---

### Post by n3tfury on 2006-05-04
Hey thanks for the reply, man. Mine's pretty similar to that, but I need to look at one that's a "virgin" ;)  

I need to start WEP from scratch.  I'd REALLY like to go WPA, but meh, that looks like a royal pain in the ***.

---

### Post by MartinJ on 2006-05-05
If no-one provides a fresh file and you have a live cd, you could load that up and copy the interfaces file from there...?

---

### Post by n3tfury on 2006-05-05
[QUOTE=MartinJ]If no-one provides a fresh file and you have a live cd, you could load that up and copy the interfaces file from there...?[/QUOTE]

I actually don't have a live cd anymore.  I gave those away trying to spread the love.  Hate to download the iso again just for that file.   :/    Thx for the idea though, bro.

---

