---
title: "Power Manager on iBook G4 w/Karmic Koala"
date: 2009-11-08
forum: Apple Hardware Users
---

### Post by schlauf on 2009-11-08
Hey there,
after some time I've decided to give Ubuntu another try on my good old iBook G4 (1.33 GHz, one of the latest models produced). Installation of Ubuntu 9.10 performed like a charm and the running system really pleases my eye after adapting some stuff to my needs (mouse key emulation etc.)

One thing seriously annoys me, though: the power manager applet does not recognize the attached battery even when power is disconnected: therefore, the system happily assumes to be running on AC power and finally shuts off without previous notice when the end of battery lifetime has been reached.

How do I fix this?

Thanks!

---

### Post by schlauf on 2009-11-09
Anybody here who can confirm their iBook G4 1.33 GHz shows up the attached battery in Gnome? Disabling gnome-power-manager did not work at all. Sadly, battery settings can not be read via acpi on command line ... :(

---

### Post by linuxopjemac on 2009-11-09
For PowerBooks it's recommended to have pbbuttonsd installed. I found a link with the right pbbuttonsd.conf for you:

[http://cmr.cx/ibook/linux/ibook_linux.html](http://cmr.cx/ibook/linux/ibook_linux.html)

Get the last version of pbbuttonsd and install it 

```
wget http://prdownloads.sourceforge.net/pbbuttons/pbbuttonsd-0.8.1a.tar.gz
tar -zxvf pbbuttonsd-0.8.1a.tar.gz
cd pbbuttonsd-0.8.1a
./configure LAPTOP=pb

make
make install
```
on file pbbuttonsd

```
/etc/rc.d/init.d/
```

change the DEAMON
```

#DAEMON=/usr/bin/pbbuttonsd
DAEMON=/usr/local/bin/pbbuttonsd
```

restart

```
 /etc/rc.d/init.d/pbbuttonsd restart
```


See also
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
[http://pbbuttons.berlios.de/projects/pbbuttonsd/doc.html#install](http://pbbuttons.berlios.de/projects/pbbuttonsd/doc.html#install)


I think you need to uninstall pommed for this to work.

---

### Post by linuxopjemac on 2009-11-09
An even older daemon for power is pmud but I recommend pbbuttonsd

[http://sourceforge.net/projects/apmud/](http://sourceforge.net/projects/apmud/)

also
[https://launchpad.net/ubuntu/+source/pmud/0.10-9.1](https://launchpad.net/ubuntu/+source/pmud/0.10-9.1)

---

### Post by linuxopjemac on 2009-11-09
I know that pbbuttonsd is still in the repository for Debian. It seems to be abandoned by Ubuntu...

---

### Post by schlauf on 2009-11-09
No chance to get it up and running with standard configuration (without installing the most recent sources)?

I hate installing additional drivers/stuff which is not subject to automatic updates on my system ... :(

---

### Post by linuxopjemac on 2009-11-10
as I said, pbbuttonsd is not part of the Ubuntu repository. If you want that, you have to switch to Debian ppc.

---

### Post by linuxopjemac on 2009-11-10
and, pbbuttonsd and pmud are no longer prone to change. They are developed and stable. They didn't change since 2007 or something. So you don't need to update these packages....

---

### Post by schlauf on 2009-11-12
Thanks, will try that ...

---

### Post by Henry Higgins on 2009-11-22
I'm having the same problem with a G3 iBook. 9.04 was working fine on it. Notably, power management worked correctly, including auto suspend after a certain time on battery power alone. However, since upgrading to 9.10, something has gone wrong with power management:

- In the Power Management Preferences, there is no longer a tab for battery settings.
- On battery power, the iBook behaves exactly as if it was plugged into AC power, despite the different settings I had for battery power (which worked in 9.04). If I don't plug in the AC power source, the computer will go on working until the battery is empty, at which point is will switch off without warning.
- If I suspend manually, the computer doesn't wake up again when a key is pressed. Nothing I have tried has worked here: the only solution seems to be a hard reboot.

I've tried reinstalling gnome-power-manager. I've tried sudo dpkg-reconfigure  gnome-power-manager. pbbuttonsd is already installed but I couldn't get it to do anything useful, even after completely removing gnome-power-manager. 

Maybe I should downgrade back to 9.04? Is there a way to do this without doing a complete reinstall?

---

### Post by ditsch on 2009-11-22
Do you have pmu_battery loaded? [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/458004](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/458004)

---

### Post by Henry Higgins on 2009-11-22
Thanks, ditsch, for your rapid reply. I added pmu-battery to the etc/modules file so it loads with the kernel. I am pleased to report that:

- There is now a battery icon in the panel.
- There is now a battery settings tab in the Power Management Preferences.

What still isn't working is waking up from suspend: the computer is frozen when I try to do this and I still have to reboot.

Any ideas?

---

