---
title: "ubuntu networking attempt--main desktop machine doesn't connect to internet"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by stairwayoflight on 2006-04-24
hi,
i am a linux/networking noob. ihad a working internet connection with 5.10 breezy desktop. everything worked with dhcp.
i have a blanc router through which i get internet access from my cable modem. this is a wireless router device, but i am hooked up through ethernet for now.

**i am having problems making sense of network howtos.**

i think its probably because the "choices" based ones assume you are good at making choices while the "cut-and-paste" ones assume the default configuration will work for you.

i am trying to set up a network as follows:

i get internet through my cable modem. i have two pcs that can potentially get it by dhcp. they are wired to my blanc wireless router through ethernet. i want to set up one as a samba server, was trying the howto at:
[www.howtoforge.com/samba_setup_ubuntu_5.10](www.howtoforge.com/samba_setup_ubuntu_5.10)

but no matter what i did i could not ping my new server.

by default my router allows network addresses from 192.168.1.0-253.
i don't know if i correctly config-d my ethernet interface file with this change; the howto assumes your home network to be using 192.168.0.1-255 I believe.

without the samba part, what do i ned to have on my 2 boxes to ping each other?
i want to login w/ ssh, etc. but for now just a ping will make me happy.

of course i would love to get my primary box back up with internet access.

---

### Post by Packard on 2006-04-24
Hi,

what is your network card? I guess it doesn't obtain an IP address. What is the output of "ifconfig"? You could also try to enter "sudo dhclient" in a shell and see what it does.

I had a similar effect with a Marvell Yukon ethernet device, but I got it to work somehow.

---

### Post by stairwayoflight on 2006-04-24
oh,

my desktop withuot internet now?

i backed up /etc/network/interfaces, then changed the config for eth0 from dhcp to static, with other stuff from the howto (i tried to change the values to reflect my network is 192.168.**1**.0.x, not 192.168.0.x) as folows:

```

...
# The primary network interface
iface eth0 inet static
address 192.168.1.98
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254

```

i know the gateway is correct becaues i can ping it from this computer. i don't know what the 'network' address means, i changed the 3rd term from 0 to 1 for 'network'.

assuming i get back up w/ dhcp on my workstation, on the same router as this machine, should i be able to set this up as a server without messing around with ip addresses on my workstation?

sory to edit, but
sudo gave error: unable to lookup fishybreakfast.net via gethostbyname()
i guess this means sudo failed, and so did the rest of the command which was supposed to restore my backup /etc/network/interfaces

i don't have a root account, and without sudo i don't think i can change cfg files right?

---

### Post by stairwayoflight on 2006-04-24
whooah!

well after all the confusion of trying to find out which values were wrong where, i found the gui network interface in ubuntu
system->administration->network
i just renamed my host/domain properly in the tab and everything worked! yay!

---

