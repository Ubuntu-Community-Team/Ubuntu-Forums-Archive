---
title: "Anonymous Searching"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-07-02
Is there any ubuntu programs that can let me search the net or even connect to the net annoymous. I can't find any for ubuntu, and I don't wanna use proxies from a list.

---

### Post by Megaqwerty on 2007-07-02
Tor is one of the highest anonymity programs I have ever come across. There is a package for it in the repository, and it's homepage (so you can learn more) is here: [http://tor.eff.org/](http://tor.eff.org/)

---

### Post by phizikal on 2007-07-02
I tried everything from this page, and none of these commads work. I am using dapper. could that be the problem?

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

---

### Post by Megaqwerty on 2007-07-02
Sorry, I didn't mean to follow their instructions :-\ 
Install tor with: ```
sudo aptitude install tor
```
You can then read the manual for it's use by doing: ```
man tor
```

---

### Post by phizikal on 2007-07-02
Okay, the first one didn't install it. Or else I can't find it anywhere.
```

root@admin:/home/admin# sudo aptitude install tor
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

The second gave me the manual, which it works.

When I try running tor.
```

root@admin:/home/admin# tor
Jul 02 01:22:43.019 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jul 02 01:22:43.057 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Jul 02 01:22:43.058 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jul 02 01:22:43.058 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

```

sorry for  bugging you. =/

---

### Post by phizikal on 2007-07-02
*cough* excuse me.

---

### Post by eternalsword on 2007-07-02
tor should already be running.  now try using the firefox extension foxyproxy.

```
ps aux | grep tor
```
should tell you if it's running

see [http://blog.mypapit.net/2007/06/how-to-setup-tor-and-privoxy-in-ubuntu-feisty-fawn.html](http://blog.mypapit.net/2007/06/how-to-setup-tor-and-privoxy-in-ubuntu-feisty-fawn.html) for more help on setup

---

### Post by Megaqwerty on 2007-07-03
> **phizikal said:**
> *cough* excuse me.
Sorry, I went to bed before I saw your message, however I recently found an application called [tork]("http://tork.sourceforge.net/wiki/index.php/Main_Page")
which is a KDE front-end to tor. (You shouldn't need to have KDE installed to run it)

To install it, run: ```
sudo aptitude install libgeoip1
wget http://download.tuxfamily.org/3v1deb//pool/feisty/3v1n0/tork_0.12-0+3v1ubuntu0_i386.deb
sudo dpkg -i tork_0.12-0+3v1ubuntu0_i386.deb

```

You can choose whether or not to keep the .deb file or not.

-Megaqwerty

---

### Post by AlexenderReez on 2007-07-03
actually if you just want to bypass firewall like school firewall.....just use [www.3proxy.com](www.3proxy.com)

---

### Post by Megaqwerty on 2007-07-03
> **reez0105 said:**
> actually if you just want to bypass firewall like school firewall.....just use [www.3proxy.com](www.3proxy.com)

That does not appear to be the intention of phizikal. The question was in hopes of not using a proxy, in the interest of anonymity.

---

