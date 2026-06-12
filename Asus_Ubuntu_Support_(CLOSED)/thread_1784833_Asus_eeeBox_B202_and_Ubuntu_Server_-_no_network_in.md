---
title: "Asus eeeBox B202 and Ubuntu Server - no network interface has been found"
date: 2011-06-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by para-banana on 2011-06-17
Hi @ all :-)

Some month ago I finally switched my desktop systems from Windows to Linux.
Now I would like to switch my server system too (previously win server 2000). I use the Asus eeeBox B202, which worked out pretty well for my windows server 2000, is silent and power-saving.

I tried to install the Ubuntu server versions 10.04 LTS and 11.04 (32 bit), but it never found a network interface during installation (neither the wired nor the wireless one). I was looking in this board and at Google for related results, but there were only issues about the wifi card. 
Installing natty works without problems and the interface is recognized, thus the server version must lack the essential drivers.
How can I install a driver for the on-board Ethernet card?
As far as I could find out, it should be the *Realtek* RTL8111C...

Thanks a lot!

---

### Post by penguinszp on 2011-08-21
Did you ever figure out what to do about the no network interface problem? I have the same issue, trying to install Ubuntu server 11.04 64-bit.

EDIT: Just noticed I do not have the same model, mine is the ASUS EB1007-B0410. Would still like to know if you found the solution to the problem though.

---

### Post by michaelb28 on 2011-08-30
Hi,

I have an ASUS Eee Box EB1007 like the 2nd poster, but with Ubuntu 10.04 server edition installed.  I remember that the network interface didn't work after installation, but I didn't have to install any drivers. I justed edited the /etc/network/interfaces file to add an entry for eth0.

I fixed it by adding these lines to /etc/network/interfaces:

auto eth0
iface eth0 inet dhcp

Later, I wanted to change to a static IP and I replaced the above with these lines:

auto eth0
iface eth0 inet static
   address 192.168.2.150
   netmask 255.255.255.0
   network 192.168.2.0
   gateway 192.168.2.1
   broadcast 192.168.2.255

Of course, you'd need to edit the numbers above to fit your network configuration.

I didn't try using the wireless interface though.

Hope this helps.

---

### Post by rsborn on 2011-10-19
This is a pretty old thread but maybe I can help. I have a Asus EEE B202 sitting on my desk that I originally installed Ubuntu 10.04 and now has been upgraded to 11.10. I don't use wireless but my wired network connection does work.

My wired card seems to be a Realtek RTL8111/8168B
Wireless is a RALINK RT2860

While I don't use the wireless interface, I do see available wireless interfaces (even without the antenna screwed in) so I would expect that it would work.

If you want to see any of my settings, by all means let me know.

Rick

---

### Post by jackbraidwood on 2012-12-17
Would you mind sharing your settings?

---

