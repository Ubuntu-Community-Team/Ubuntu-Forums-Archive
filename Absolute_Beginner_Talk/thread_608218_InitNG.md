---
title: "InitNG"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-09
i want to use initNG, so i followed the guide on ubuntu docs, or whatever

when i boot it syhows i have no internet connection, and no services are availble.

is there a good walkjthrough of what to do?

---

### Post by skymera on 2007-11-09
ok scrapt that

just got rid of all initng file and removed them from synaptics.

but now my internet does not work :(

firestarte says wlan0 is not ready, i have no idea what to do..

i tried ifconfig, im also not recieving any DHCP offers, probably due to it 'not being ready'

any ideas?
im gettin a tad pi**ed off with all these stupid network problems..

---

### Post by skymera on 2007-11-09
itf it helps

in ifconfig
i had

eth0
wmaster0
and wlan0

wmaster0 is now gone, and dosent come up, does this have anything to do with it?

---

### Post by phantom74 on 2008-02-11
do you obtain ip from a dhcp server?

if so, insert this command in the shell: dhclient 

and examine the output if it doesnt work.

if you have a static ip address do the following:

ifconfig eth0 your.ip.addr.ess 

if your behind a router, just enable the DHCP server and follow the first step:

in the shell type: dhclient

wait a moment and you will have a lesed ip from the dhcp server.

anyways, my guess is that you have no way of starting up scripts since you uninstalled initNG.

im a noob so, i think you better recover the system if this option doesnt work for you.

---

### Post by skymera on 2008-02-11
thanks for the post but this is from 2007 :)

---

