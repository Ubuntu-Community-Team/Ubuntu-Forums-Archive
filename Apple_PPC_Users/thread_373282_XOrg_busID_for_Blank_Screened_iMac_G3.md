---
title: "XOrg busID for Blank Screened iMac G3"
date: 2007-03-01
forum: Apple PPC Users
---

### Post by SquidThing on 2007-03-01
When trying to **startx** on an iMac G3 running Ubuntu Server 6.10 with the xubuntu-desktop package, I get sound but only a black screen.

I'm fairly sure this is because the xserver has failed to properly indentify my graphics card (an AGP ATI Rage Pro 128 @ busID 0000:00:10.0)

Now that **lspci -X** has gone, how can I convert the result of **lspci -n** into something that can be entered into **dpkg-reconfigure xserver-xorg**?

**lspci -n** returns:

0000:00:10.0 0380: 1002:5052

regards,

Andrew

---

### Post by macmatt on 2007-03-12
It's because Mac's were designed to be used with the best OS ever - their very own Mac OS!. Ubuntu is in it's infancy, and is a tedious bore. Therein lies the answer. Ever get a Vauxhall engine, fitted inside a Ford, without *any* hassle?

LOL!!:lolflag:

---

### Post by 3rdalbum on 2007-03-13
> **macmatt said:**
> It's because Mac's were designed to be used with the best OS ever - their very own Mac OS!. Ubuntu is in it's infancy, and is a tedious bore. Therein lies the answer. Ever get a Vauxhall engine, fitted inside a Ford, without *any* hassle?

LOL!!:lolflag:

Thanks for trolling.

Squid, if you're still here, you don't need to put anything different into the Bus ID in dpkg-reconfigure xserver-xorg. Xorg does a fine job of detecting the card; the bit it gets hung up on is the monitor's settings.

Use sudo nano /etc/X11/xorg.conf to open the configuration file, and then change your Section "Monitor" part to the following:

```

Section "Monitor"

    Identifier "Generic Monitor"
    Option "DPMS"
    HorizSync 60-60
    VertRefresh 43-117

EndSection
```

Save and quit Nano, then restart GDM (sudo /etc/init.d/gdm restart).

---

