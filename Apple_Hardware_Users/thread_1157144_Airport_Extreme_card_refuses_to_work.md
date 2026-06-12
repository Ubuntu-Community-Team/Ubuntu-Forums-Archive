---
title: "Airport Extreme card refuses to work"
date: 2009-05-12
forum: Apple Hardware Users
---

### Post by colinhayes on 2009-05-12
So I can no longer get my airport extreme card to work under Ubuntu.  I have a linksys router with DDwrt in mixed  B&G mode with a WPA personal password. (I am not willing to change from WPA)  Yesterday I hauled the computer over to the router,updated to 9.04 (btw, only update since 6.10 that hasn't killed my display!!), did the driver activation, and let it download the stuff.  

Didn't work.

followed the instructions on [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) and it still won't do a thing.

the networking icon in the top menubar notes that the wireless device is unmanaged.  I can input my network information in as a new wireless connection, but it will never connect.  syslog does not show any errors.  This is all on a Dual 2GHz Powermac G5 from June '04.

Any ideas?

---

### Post by stream303 on 2009-05-12
> **colinhayes said:**
> followed the instructions on [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) and it still won't do a thing.

Are you using Network Manager to control networking, or are you using just the standard Ubuntu Networking dialogs in System > Administration > Network?

I'd recommend using Network Manager now that it is up to ver 0.7 which works MUCH better than before.

Thing is, if you do run Network Manager, your /etc/network/interfaces file should ONLY contain these items:

```
# The loopback network interface
auto lo
iface lo inet loopback
```

If you have anything more than that, NM won't work properly as it fights with the standard networking setup.  I've seen a lot of confusion over this - you either run NM and let it do it's thing with that very minimal /etc/network/interfaces file, or you don't have NM installed at all and have a fully-populated interfaces file.

The B43 firmware cutter provided with 9.04 should work well - you should be prompted with the proprietary software notification, or go into the proprietary hardware setup and "activate" it - which will download the firmware cutter and perform the install for you.

It is possible that the "upgrade" got confused in regards to this, rather than the clean-install method.  (This is what I did on my G5 iMac with Airport Extreme, although I'm running a Netgear wireless usb stick now for ethical reasons.. )

> This is all on a Dual 2GHz Powermac G5 from June '04.

That's a great machine, and since it is running the nvidia card, you also have the option of installing the "nouveau" driver which can replace the default nv driver if you so choose.  (Still 2D only, but a fully free project).

Worst case - save your existing /etc/X11/xorg.conf, and do a clean install.  But I'd try running NM with a minimal interfaces file, and perhaps reinstalling the B43 firmware cutter provided with 9.04 itself...

---

### Post by colinhayes on 2009-05-12
actually, it's an ATI Radeon 9600 xt graphics card... I think the previous generation (the very first that were in production for about 2-3 months) of G5's had nvidia cards, maybe, but i'm probably wrong.

I'll try NM, that's what I'm used to and it's what I couldn't find.  It worked before when I had NM and then it went to this new network configutator it done stopped workin'!

---

### Post by colinhayes on 2009-05-12
ok so nm-applet is the exact same thing as system>preferences>network connections, and it doesn't work.  I altered the interfaces file and that didn't help.

so, um, what next?

---

### Post by stream303 on 2009-05-12
Well, if it were mine, I'd do a fresh install, rather than rely on upgrades.  Upgrades on ppc were always kind of a risk, although some were able to manage a 6.06 > 8.04 transition.

You have enough horsepower to support the live Desktop-CD for install, although my favorite is the "alternate" text-based installer.  Both can be found:

[http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

Note that even though my G5 iMac had enough horsepower to run the Desktop installer, it wasn't until after I had actually installed the system, *and performed the updates via System > Upgrade Manager* that I was able to just "activate" the b43-firmware cutter with the proprietary utility.  WPA2 no problem.

(although I had a change of heart and am now using a Netgear WG111v2 usb stick - no firmware needed)

Other than this, the only quickie things I could think of to try with that system in an unknown-upgrade state, would be to:

1) Try disabling wireless in NM, and enabling it again.

2) If you have an existing connection in there listed, delete it and start over.

More than this would be to see if your card is even up in the first place if you have the *wireless-tools* package installed:

```
sudo iwlist wlan0 scan
or
sudo iwlist wlan1 scan
```

You may be able to get more help from the networking forum, but personally I'd start from a clean state with a fresh install rather than the upgrade state.

---

### Post by colinhayes on 2009-05-12
> **stream303 said:**
> 
1) Try disabling wireless in NM, and enabling it again.

2) If you have an existing connection in there listed, delete it and start over.


I don't even want to count how many times I tried both of those already...


I think I'm going to wipe the hard drive completely (it is a secondary drive) and start over, especially since when I first formatted the drive about 4 years ago, I gave 130GB to the Ubuntu partition, which has permanently had well over 100GB free!  that space can be much better used as part of my 10.4/classic/backup/time-machine partition.  I can't think of anything better to do than drink beer and work on my computer right now, anyways.

EDIT: booted back over to copy essentials and it's working now... go figure.  I might wipe the drive anyways, though.

---

### Post by stream303 on 2009-05-12
I hope I caught you in time -

Whenever you are doing a reinstall from a working setup, be SURE to copy or print out these files *off the machine somewhere else*

/etc/yaboot.conf

/etc/X11/xorg.conf

/etc/fstab

Looking forward to a fresh 9.04 up and running on that box!

---

### Post by colinhayes on 2009-05-12
i printed off xorg and yaboot as I had a fanciful triple boot system, but now it boots to a black screen after I tell yaboot to go into linux and ctrl alt f1 doesn't bring up a terminal.... kinda stuck now.

---

