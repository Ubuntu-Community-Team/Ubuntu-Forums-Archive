---
title: "ubuntu/edubuntu"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-07-04
what is the difference between those two, and if there are none, why have two names?

---

### Post by Nekiruhs on 2007-07-04
> **supersonicdarky said:**
> what is the difference between those two, and if there are none, why have two names?
Edubuntu has educational apps preinstalled and a different theme.

---

### Post by dbott67 on 2007-07-05
In addition to what Nekiruhs posted, here's a snippet I posted in another thread:
> **dbott67 said:**
> You may already be aware of some or all of this, but it may help future people that find this thread, so I'll try to explain things as thoroughly as possible.

Edubuntu is basically built on 2 things: **Ubuntu** & **LTSP** (Linux Terminal Services Project)

LTSP allows 'thin client' (PCs or network devices with limited CPU power, low RAM & no hard drive) to connect to the server and run a Windowed environment. The benefit is that the server does all the heavy lifting, and the client is really just for displaying what's happening on the server.

In order to allow the clients to connect, Edubuntu is configured to run it's own DHCP server that provides each client an IP address during boot, as well as where to get the PXE/boot image. From there, the kernel is loaded into memory and the client PC will eventually reach the login screen.

The clients can connect to the server using a number of methods:
- PXE-enabled network cards (they can automatically obtain an IP and download a PXE/boot image from a server)
- Boot disk (floppy, CD-ROM, Hard disk, USB, etc.)
- Fat-client: install an OS (Windows, OSX, Linux, etc.) and then use a secondary application to connect to the server (examples would be: Citrix, NX Machine, Xnest, TSClient, etc.)

If your kid's PC does not have a PXE-enabled NIC, just use [ROM-O-MATIC]("http://rom-o-matic.net/5.4.3/").  I tried it out last week and it works great.

When the thin client connects, the client PC gets essentially gets connected to a secondary installation of Ubuntu (contained in a "[chroot]("http://en.wikipedia.org/wiki/Chroot")" directory). The server has one install that contains whatever apps & services the server needs and the "clients" get connected to the "chroot" installation, which can contain different applications and different window mangers, if desired (such as Gnome, KDE, etc.). Whenever you want to work on the "client" installation, you need to type the following command on the server:
```
sudo chroot /opt/ltsp/i386
```Once that's done, you'll be in the "client installation" and you can run commands like apt-get to install new apps, etc.

You can read the rest of the post here:
[http://ubuntuforums.org/showthread.php?p=2961166#post2961166](http://ubuntuforums.org/showthread.php?p=2961166#post2961166)

-Dave

---

