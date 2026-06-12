---
title: "booting with 2 video cards, can't start gnome or x server"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by cogoswsds on 2007-06-02
I have a computer which had Windows XP SP2 on it.  One of the DLL files is corrupt and I cannot find the XP restore disks.  So I thought I would give Ubuntu 7.04 a try.

This machine is an old E-machine T1140 with two video cards installed.  One is the on-board video, the other is an NVidia GeForce 4 MX4000.  The NVidia card was configured as the primary display under XP.

The Ubuntu LiveCD goes partway through the boot process using the NVidia, then for some reason switches to the on-board video, which is apparently incompatible as all I have on the screen is a few rows of static.  When I try to boot with safe video mode, it stays on the NVidia card but then tells me it cannot start the X server.  The error messsage I get is:

[B](==) Log file: /var/log/Xorg.0.log" Time: Sat Jun 2 18:02:22 2007
(==) Using Config file: "/etc/X11/xorg.conf"
(WW) VESA: No matching device selection for interface (BusID PCI:1:14:0) found
(EE) VESA(0): Cannot read V_BIOS
(EE) Screens found, but none have a usable configuration.

Fatal server error: no screens found.

The X server is now disabled.  Restart GDM when it is configured correctly.
[/B]

How do I configure the X server to use the NVidia card and restart GDM so I can install this on my computer? (Remember, I'm working from the LiveCD here).  The computer does have internet access, as I see the computer running Ubuntu in the DHCP table on my router when I look at the router from a different computer).

Cogoswsds

---

### Post by bodhi.zazen on 2007-06-02
> **cogoswsds said:**
> I have a computer which had Windows XP SP2 on it.  One of the DLL files is corrupt and I cannot find the XP restore disks.  So I thought I would give Ubuntu 7.04 a try.

This machine is an old E-machine T1140 with two video cards installed.  One is the on-board video, the other is an NVidia GeForce 4 MX4000.  The NVidia card was configured as the primary display under XP.

The Ubuntu LiveCD goes partway through the boot process using the NVidia, then for some reason switches to the on-board video, which is apparently incompatible as all I have on the screen is a few rows of static.  When I try to boot with safe video mode, it stays on the NVidia card but then tells me it cannot start the X server.  The error messsage I get is:

[B](==) Log file: /var/log/Xorg.0.log" Time: Sat Jun 2 18:02:22 2007
(==) Using Config file: "/etc/X11/xorg.conf"
(WW) VESA: No matching device selection for interface (BusID PCI:1:14:0) found
(EE) VESA(0): Cannot read V_BIOS
(EE) Screens found, but none have a usable configuration.

Fatal server error: no screens found.

The X server is now disabled.  Restart GDM when it is configured correctly.
[/B]

How do I configure the X server to use the NVidia card and restart GDM so I can install this on my computer? (Remember, I'm working from the LiveCD here).  The computer does have internet access, as I see the computer running Ubuntu in the DHCP table on my router when I look at the router from a different computer).

Cogoswsds

LOL

IMO the easiest and fastest way is with the envy script.

First you need to enable your repositories :

See here : [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

You will have to use nano as X is not working.

At the command line : ```
sudo nano /etc/sources.list
```

_Note_: That is a small "L" and not the number 1

Remove the # from the front of the appropriate lines (like in the link I gave you). It is OK if you do not have all the lines in that link, so other then removing a few # you DO NOT need to add any lines.

Then, you can download the file you need with :

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.3-0ubuntu6_all.deb
```

Then install the driver with :

```
sudo /etc/init.d/gdm stop
sudo dpkg -i envy*.deb
sudo apt-get install -f
sudo envy -t
```

If you have questions go here :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

And here :

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

And post with questions back here.

Then :

```
sudo /etc/init.d/gdm start
```

---

### Post by bodhi.zazen on 2007-06-02
:lolflag:

I *should* have mentioned that it may be easier to install from the alternate CD, then update the nvidia driver as above post install once you boot to the hard drive :)

---

### Post by cogoswsds on 2007-06-02
Wow that was a fast reply!

I'm almost there, I just have one error.  I get a whole bunch of error messages about various modules not being installed that envy depends on when I **sudo dpkg -i envy*.deb**.  I go on to the next step anyway, which is the **sudo apt-get install -f** command, and it goes and gets a whole bunch of stuff.  Then I retry the **sudo dpkg ...** command and I get one error message saying that package module-assistant is not installed.  How do I install this package?  Remember, I'm just running the Live CD at the moment and I'm trying to get the GUI working so I can install it on the machine, at which point I may be doing this all over again.

Thank you for your help so far!  I feel like I'm almost there!

CogoSWSDS

---

### Post by bodhi.zazen on 2007-06-02
Well, module-assistant is in the repositories (universe), so my first guess is to look at /etc/apt/sources.list and make *sure the line with universe in it is uncommented (lines with a # at the start are comments. Two ## are for configuration so leave those alone.

If your repos are OK, ```
sudo aptitude update
sudo aptidtude install module-assistant
```

Post any errors ...

BUT I would again point you to the alternate CD ...

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

he he he ... Don't let al that stuff intimidate you, boot the alternate CD and follow along with the pictures :)

Post install we can fine tune X

---

