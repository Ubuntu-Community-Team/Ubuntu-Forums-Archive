---
title: "install ubuntu via network"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by j0nes on 2007-10-15
I have a question about installing Ubuntu onto a computer via my home network.

I have an older machine with only a CD drive, but i have Ubuntu on a DVD disc.

I'm wondering if it's possible to run the DVD on my laptop and have Ubuntu install over the network onto my other computer.

The BIOS on this other machine has an option to set the first boot device as "network" so i'm wondering if that will make it possible. Any help would be greatly appreciated.  Thanks in advance.

---

### Post by ruibernardo on 2007-10-15
Hi J0nes,

I don't know about installing directly from the DVD on the laptop to the other machine, but you can install from the network. Take a look here: [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by j0nes on 2007-10-16
Hello epimeteo, thanks for the link, i checked it out and it seems to be close to what i want to do, except for one thing.

One of the first steps is to add the following info to my DHCP server...

      In /etc/dnsmasq.conf, add the line:

  dhcp-boot=pxelinux.0,roo,172.31.0.252

My DHCP server is just a typical 4 port D-link router, not another machine running any type of tweakable operating system.

---

### Post by ruibernardo on 2007-10-16
Since you have a network with a router and you can boot with CD on the old PC (with the [the minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD")) you could try this one:

[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)

It is more simple and doesn't make any change to you network, just an apache2 install in the server (laptop).

Hope this one helps. :)

---

### Post by drascus on 2007-10-16
If its an older computer you could always download the alternate install .iso file and burn it to a normal blank CD. This would eliminate the whole DVD problem altogether... If the computer has enough ram you could alternatly download the regular .iso file and that would also work.

---

