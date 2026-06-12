---
title: "setting up wireless web connection via router"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-12-30
My ethernet connection, which is directly part of the motherboard, has failed and I am now trying to set up a wireless connection to my provider with a usb  dongle. The router and the dongle both work as they are used to connect my wife's set up to the web which I am using to write this.
I have Gutsy and I am not having any success so far. Can anyone help or point me in the direction of a help file? I guess I was lucky with the ethernet connection as Gutsy found it straight away.

---

### Post by cmnorton on 2007-12-30
What version of Ubuntu are you running? If it's 7.04 or 7.10, use NetworkManager, which works quite well, at least in my experience. 

Assuming your system is set up to get its ethernet address from DPCP:

I would back up /etc/network/interfaces like this

sudo cp /etc/network/interfaces /etc/network/interfaces.manconfig

Then, I'd edit /etc/network/interfaces, so it has these lines only:

auto lo
iface lo inet loopback

(sudo vi /etc/network/interfaces or use your editor of choice.)

Restart networking:

sudo /etc/init.d/networking restart

and start debugging this problem from there.

---

