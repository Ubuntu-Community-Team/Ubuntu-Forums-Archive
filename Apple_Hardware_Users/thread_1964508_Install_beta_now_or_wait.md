---
title: "Install beta now or wait ?"
date: 2012-04-24
forum: Apple Hardware Users
---

### Post by Dr. McKay on 2012-04-24
I'm a little anxious to install Ubuntu 12.04, but it's still in beta. If I install the beta now, will it update itself afterwards to the final version, or will I have to redownload the final version and reinstall ?

---

### Post by garak on 2012-04-24
> **Dr. McKay said:**
> I'm a little anxious to install Ubuntu 12.04, but it's still in beta. If I install the beta now, will it update itself afterwards to the final version, or will I have to redownload the final version and reinstall ?

Go and install it now.
Differences between current beta and final release are equals to differences between final release and final release + few days.
Of course, you don't need to reinstall anything, you'll just do normal upgrades

---

### Post by prshah on 2012-04-24
I've upgraded 2 days back. Everything is great, and I find Gnome much smoother now than before (Gnome3).

I faced problems in offline (CD) upgrade, but online upgrade went very smoothly, though it took a lot of time.

I'd recommend beating the rush of the "official" release and upgrading now.

To upgrade on a running system, give the following command from the Terminal (Applications-Accessories-Terminal)```
sudo "update-manager -d"
``` Quotes are important, sometimes the -d activates "debug" mode on sudo instead of being applied to the update-manager command.

After completing the update, it will continue to update itself normally, including any changes to the "final" version. In other words, it will reach the same level as if you wait for the final release to upgrade.

Also recommended to use DE specific sudo; eg gksudo, kdesudo, etc as applicable.

---

### Post by Dr. McKay on 2012-04-24
I'm on a 2.8Ghz C2D iMac, one partition Snow Leopard, I had Ubuntu 11.10 on it before (with refit) but had to remove because of lack of space. 
I've moved a lot of stuff to an external drive and will be partitioning and installing tonight I think...

---

### Post by Dr. McKay on 2012-04-24
Problem downloading 64-bit version :
[http://ftp.ticklers.org/releases.ubuntu.org/releases//precise/ubuntu-12.04-beta2-desktop-amd64.iso](http://ftp.ticklers.org/releases.ubuntu.org/releases//precise/ubuntu-12.04-beta2-desktop-amd64.iso)

Edit : never mind...

---

