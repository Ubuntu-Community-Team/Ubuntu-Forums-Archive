---
title: "Hoary live cd boots, now what?"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by ubuntubrian on 2005-04-10
I posted this on another thread but after no responses I though maybe a new one. I couldn't decide if I should post here or on the mac/pppc forum. Anyway...
I would like to mount my hd on the gnome desktop and access my files on it. When Ubuntu boots fromthe cd it shows as detecting airport and the modem but I cannot for the life of me figure out how to set up my network settings to use either. Is there a decent tutorial that will walk me through the setup? I'm spoiled with Panther's ease (I just configured my wife's new ibook). Do I need domain addresses and all of that arcane stuff and why won't ubuntu autodetect my modem port? How do I enable Airport to get online? so many questions and I so want to get moving toward linux (now a fink user, which is great except their packages tend to be a bit outdated). I have resisted repartitioning my hd and installing ubuntu there so I really want the live cd to work for me. I see many other posters who use the ;ive cd as their distro and it seems ideal-for now.
G4 TiBook 15"
Panther 10.3.8
1Ghz
784Mb ram
superdrive


  *

---

### Post by Rxke on 2005-04-11
Do you use airport or airport extreme?
Airport extreme does not work, sadly.... airport plain vanilla does.

---

### Post by ubuntubrian on 2005-04-11
just vanilla. I know the hardware is detected when ubuntu boots but how do I actually use airport on ubuntu?
thanks

---

### Post by Rxke on 2005-04-11
If I recall correctly, the setup shows you a list of ways to connect to the net... eth0 and eth1 being amongst them. eth0 is the ethernetport, and eth1 should be your internal Airportcard.

then it asks how to connect, select DHCP, if your airbase or other wireless hub is active, it should auto-connect. 

Then it asks for the name of your airport/hub/network errr... thingie. That's sometimes just a number, like 7655445. if you use encrypted wifi, it then also asks for your WEPpassword.

This is from memory, so i'm totally unsure I'm accurate, but maybe it helps?

---

### Post by Rxke on 2005-04-11
Oh, I forgot: if you're still in OSX, you can look up the name of your network under system preferences> network. if you select network status, it should list your Airport with a comment somewhal like "Airpport is connected to network "name-of-network"

---

### Post by ubuntubrian on 2005-04-11
Thanks, I'll try that next time I'm at my favorite bakery that has a network. I'd still like to know how to set up for ubuntu to rcognize my modem for dial-up (at home) as well as how to get my hd mounted on the ubuntu desktop. Do I need to create a disk image of the hd and mount it first in OSX?

---

