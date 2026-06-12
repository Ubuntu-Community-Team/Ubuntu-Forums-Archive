---
title: "No wireless when I boot"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by kjacks on 2005-12-11
Hi guys, 

I just installed Ubuntu on my laptop and I love it!  The tutorials for repartioning my windows drive worked great and the Ubuntu install was very easy.  

The only problem I had was durring the install I typed my wireless key wrong and couln't access the internet.  Under system>administration>networking I corrected the WEP key and it works fine.  But when I rebooted my laptop I had to change my WEP again.  How do I save this so it logs into my network while booting up?

Thanks for the help!

---

### Post by Zelut on 2005-12-11
You can take a look at your networking file (if you're not too terrified of the terminal).  See what is listed in /etc/network/interfaces (ie; sudo gedit /etc/network/interfaces).  I believe that should store the WEP key.  If it is not listed there, or listed wrong, try editing that.  Let me know if you still need some tips..

---

### Post by kjacks on 2005-12-13
Still no luck.  The file you mentioned does have my correct WEP key.  To get my wireless working I need to click on my wireless connection> properties and add my WEP key(it shows as empty) then activate my wireless.  Thanks for taking a look at this for me.  This is what the file reads when I first log on:

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
	wireless-essid etto
	wireless-key1 
	wireless-key 1234-1234-12

auto eth0

---

