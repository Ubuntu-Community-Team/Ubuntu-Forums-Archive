---
title: "BitTorrent not working"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Toukejin on 2006-10-07
Hello all,

First let me say that I am an absolute linux beginner, and I've only been trying to set this thing up for a few days.

I'm trying to get BitTorrent working on a Dell Inspiron 600m (ethernet, not wireless), and neither the Azureus that I somehow managed to install nor the built-in BitTorrent utility will download anything.  They'll load the torrents as if everything is fine, but except for a few short jumps into the 10b/s range, I get nothing up or down.

It's not the router, I'm running DMZ.
It's not the torrents, I'm running several and all are well seeded.
It's not the ISP, Azureus downloaded fine under Windows.
I can download direct http at full speed.

I've forum searched, and I know there are Azureus issues, so it's ok if I can't get that working.  All I need is some kind of BT program.

Thanks.

---

### Post by Josh1 on 2006-10-07
Hi,
Make sure that the port is allowed on your box. Best way is to download and install firestarter (firewall) :

Load terminal (Applications>Accesories>Terminal) and type in these commands 1 line at a time.
```
sudo apt-get install firestarer
```

Or, try ktorrent. I find I like it better then azureus.
```
sudo apt-get install ktorrent
```

Both will need universal repositeries.
To enable this:
```

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

```
Find the universe line and remove the #.
For example:
```

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

```
Would probably look like:
```

#deb http://archive.ubuntu.com/ubuntu dapper universe
#deb-src http://archive.ubuntu.com/ubuntu dapper universe

```
Remove the #.

Hope this helps,
Goodluck,
Josh

---

### Post by Toukejin on 2006-10-13
Ok, sorry for the delay.

I've done all that, and KTorrent seems to be having the same problem.  I look in the event log in Firestarter and there are all kinds of blocked connections.  I think I've allowed the BitTorrent stuff, but I've got a lot of Samba, dhcp, and ssdp blocks.  The dhcp and ssdp are from the router and Samba from some other internal ip.  Does that mean its not a BitTorrent or linux problem, but rather a computer-router communication problem?  I've read through the Firestarter documentation but didn't see anything that helped.  I'm using a Linksys WRT54G, connected via cable.  Any ideas?

Thanks.

---

### Post by Toukejin on 2006-10-13
Scratch that.  I managed to lock myself out of the router, ended up resetting it, and now I'm downloading normally.  I still have no idea what the problem was though...

Thanks for all the help.

---

