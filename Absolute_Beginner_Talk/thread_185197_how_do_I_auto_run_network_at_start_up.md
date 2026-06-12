---
title: "how do I auto run network at start up?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by mike_m on 2006-05-31
I've got my wifi network working :p but with each boot up I have to start the network (eth0) manuly,  how can I get it to run at start up?

Thanks, Mike

PS it's in the panel (sys tray) only at each boot it has a red X till I start it.

---

### Post by damianubuntu on 2006-05-31
Not sure, but have a look at section 3.5 in:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

It might give you some leads whilst your waiting for someone who knows what they are talking about to answer!

---

### Post by Dr. Nick on 2006-05-31
look at the file /etc/network/interfaces and make sure that auto is next to your wifi. If you are using ndiswrapper then add ndiswrapper to the file /etc/modules

---

### Post by mike_m on 2006-05-31
thanks - this is what I got...

=======
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid 

auto eth0

========
so I guess my network should be auto, but it don't go online till I click it.
is there anything else I can do?

Thanks, Mike

PS, I just remeberd that when I do start the network I also have to type in my password, could that be the prob?

---

### Post by mike_m on 2006-06-04
Update! 
Everyone might find this instersing....
today I downloaded Xubuntu 6.06 & installed on a spare HD & on boot the network started right up, Right "out of the box"
Ubuntu 5.10 didn't work that good & even though I upgraded to Ubuntu 6.06 my network wouldn't start auto.

Wonder if a fresh download / install of Ubuntu 6.06 would work "out of the box"?
Maybe I'll try & post back, but first I'll poke around on this Xubuntu 6.06,
seams to run faster on my old Dell :)

---

