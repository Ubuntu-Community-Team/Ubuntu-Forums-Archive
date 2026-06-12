---
title: "Arch Network Problem"
date: 2008-03-13
forum: Arch and derivatives
---

### Post by Dr Small on 2008-03-13
Ok, so I finally got Arch downloaded and installed, and noticed right off the bat that it is not recognizing my network connection. I have a Dlink wireless G card that works with Ubuntu and every other distro, but I think I need to configure it in Arch.

So... where do I begin ? :)
I've mainly been reading on Archux, but haven't seen anything on network setup.

By the way, I'm running this in VirtualBox.

Dr Small

---

### Post by finferflu on 2008-03-13
Check the [Beginner's Guide](http://wiki.archlinux.org/index.php/Beginners_Guide) first, it's the first step to take. 
I don't know if the VirtualBox might be causing problems..

---

### Post by fwojciec on 2008-03-13
> **Dr Small said:**
> Ok, so I finally got Arch downloaded and installed, and noticed right off the bat that it is not recognizing my network connection. I have a Dlink wireless G card that works with Ubuntu and every other distro, but I think I need to configure it in Arch.

So... where do I begin ? :)
I've mainly been reading on Archux, but haven't seen anything on network setup.

By the way, I'm running this in VirtualBox.

Dr Small

If you're using Arch in virtual box don't try to set up the wireless card directly, but simply set eth0 to use dhcp (the most simple possible setup for wired network).

Because Arch is installed in VirtualBox it doesn't have access to your actual hardware, but uses what is provided by VirtualBox instead.

---

### Post by Dr Small on 2008-03-13
Thanks for the help :)
I commented out the other eth0 entry in /etc/rc.conf and added:
```
eth0="dhcp"
```

Still no go after reboot, so then I tried:
```
dhcpcd eth0
```

And then pinged google and all worked :)
Ok, I'm still reading around for this one, but how do I get networking to work on boot? Maybe just add:
```
dhcpcd eth0
```
To rc.conf, or is there a more graceful way?


Edit,
Also, when I try to use pacman to install xorg, I get this:
```
# pacman -S xorg
warning: current locale is invalid; using default "C" locale
error: 'xorg' not found in sync db


```

Dr Small

---

### Post by fwojciec on 2008-03-13
In addition to the line you've added to rc.conf (which defines what to do with eth0 device) you also need something like:
```
INTERFACES=(eth0)
```
which should activate eth0 on startup.  You also need the "network" daemon in the daemons array.

That should work -- in theory at least.

---

### Post by fwojciec on 2008-03-13
> **Dr Small said:**
> Also, when I try to use pacman to install xorg, I get this:
```
# pacman -S xorg
warning: current locale is invalid; using default "C" locale
error: 'xorg' not found in sync db


```

Locale issue is best explained in the wiki: [http://wiki.archlinux.org/index.php/Locale]("http://wiki.archlinux.org/index.php/Locale")
As for xorg not being found in the database -- make sure that you sync the database is synced (pacman -Sy).

---

### Post by Dr Small on 2008-03-13
Ok, thanks. That fixed my network on boot problem, and I fixed the "db sync" error by running:
```
pacman --sync --refresh
```

Cheers!
Dr Small

---

### Post by Dr Small on 2008-03-13
Thanks again.
I uncommented ```
en_US.UTF-8      UTF-8
```
in /etc/locale.gen

And then ran:
```
locale-gen
```

Which fixed my problem :)

Dr Small

---

### Post by miggols99 on 2008-03-14
I recommend using the new [network scripts](http://wiki.archlinux.org/index.php/Network_Profiles) if you are using wireless. You can also refer to my [guide](http://archux.com/page/setting-wireless-networking)

---

### Post by Dr Small on 2008-03-14
Thanks for the info. I did in fact try out your guide after I found it, but it didn't work due to eth0 and I was in VirtualBox I guess.

The next time I have a crash (fortuantly, but unfortuantly, that is rare :p) I plan to install Arch and learn it completely.

Dr Small

---

