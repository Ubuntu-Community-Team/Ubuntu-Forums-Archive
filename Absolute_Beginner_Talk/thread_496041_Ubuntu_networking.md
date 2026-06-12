---
title: "Ubuntu networking"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by frankwright1 on 2007-07-08
Hello - Lovin the ubuntu ethos!

Please can somebody help a complete novice - and one not particularly computer literate - this probably sounds a bit dumb but i hope someone out there can help.

I connect to the internet wirelessly, but my flat mate runs an apple mac (osX) with no wireless capabilities. I've spent the last two hours trying to get the mac and ubuntu to network so the mac can use the internet and for file sharing by using an ethernet cable- but im having real difficulties. The mac asks for all sorts of info like IP (does this mean the mac, ubuntu or my router?), subnet mask - haven't got a clue what this is? router address and DNS hosts?????

On the ubuntu front I'm sorry I haven't a clue - I cant see anything under places-network when i click on windows network. I tried to install this thing called gsambad that i read about on this forum thinking it may help but it doesn't open with an error reading 'Failed to execute child process "su-to-root" (No such file or directory)'

I feel like i'm blindfolded in a dark alley! I really hope someone out there can help as i don't want to throw in the towel and go crawling back to microsoft with my tail between my legs!

Many thanks
Frank

---

### Post by reset3x on 2007-07-08
To link the two machines together you would need a CAT5 Crossover cable.. Not just a regular CAT5 cable.... Do have have one?

---

### Post by steve.horsley on 2007-07-08
In addition to using a crossover cable instead of your usual ehternet cable, you will need to:
1: configure a different network number on this cable, both at the Ubuntu and the OSX ends. Can I suggest that you configure the Ubuntu ethernet port with address 192.168.99.1, netmask 255.255.255.0, and the mac with 192.168.99.2, netmask 255.255.255.0 and a default gateway of 192.168.99.1. With this done, and the right cable, they should be able to ping each other, and share files with samba.

2: Configure Ubuntu to enable IP forwarding, with this command:
**sudo echo 1 > /proc/sys/net/ipv4/ip_forward**

3: configure IP masquerading. The following command should do it, but replace "eth0" with whatever the interface name of your wireless connection is.
**sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE**


To share files, you need to install package samba (gsambad is a GUI for configuring samba). Don't bother with this until you have at least completed step 1 above and they can ping each other.

---

### Post by frankwright1 on 2007-07-09
Looks like the cable is my first step - then I'll have a go with steve's suggested commands.

Thanks guys!

Frank

---

