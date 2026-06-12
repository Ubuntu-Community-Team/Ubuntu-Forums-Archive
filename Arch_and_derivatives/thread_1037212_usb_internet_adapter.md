---
title: "usb internet adapter"
date: 2009-01-11
forum: Arch and derivatives
---

### Post by Mr.Macdonald on 2009-01-11
I have finally gotten arch linux to boot. but now I need to get internet, I am using a Netgear Prism_2 usb wifi adapter. I have wlan_ng installed.

I can see the device from `lsusb` but when I try to use
/etc/rc.d/wlan restart
It fails claiming there isn't a wlan0 device. And their isn't under /dev. Should I symlink the usb dev file to /dev/wlan0?

And if so, how would I know which usb dev file to link?

---

### Post by kerry_s on 2009-01-11
first type:
**iwconfig**

that will show you the device. go here:
[http://wiki.archlinux.org/index.php/Wireless_Setup](http://wiki.archlinux.org/index.php/Wireless_Setup)

put your settings everywhere when you get it working, i recommend netcfg to keep it solid.

i put mine in all the places, it always starts on boot.

---

### Post by Mr.Macdonald on 2009-01-11
I rebooted in hope of having the wireless be detected, and it was. But I couldn't connect to the internet so I tried to restart the wlan (/etc/rc.d/wlan restart) and wlan0 disappeared from iwconfig.

So I rebooted again, and now my drive mounts as read only, why?

I didn't change anything, and I won't be able to post results, because my Arch Linux doesn't have internet!

---

### Post by Mr.Macdonald on 2009-01-11
Update: I found out why my drive was readonly, something delete the first part of my fstab!!!

So thats fixed but internet still isn't

---

### Post by smartboyathome on 2009-01-11
I would recommend getting WICD (if you can connect via ethernet, do that). WICD works flawlessly where netcfg and iwconfig fail.

---

### Post by Mr.Macdonald on 2009-01-11
can I use WICD without a Desktop Environment, I have only command line booting. I would rather have internet work at command line and then install a desktop.

And I can't use ethernet, only the CD.

---

### Post by smartboyathome on 2009-01-11
> **Mr.Macdonald said:**
> can I use WICD without a Desktop Environment, I have only command line booting. I would rather have internet work at command line and then install a desktop.

And I can't use ethernet, only the CD.

It is a GUI app, so it can't be used without at least X and GTK (it isn't DE dependant though :)).

---

### Post by Mr.Macdonald on 2009-01-11
I still need a means of connecting via commandline

---

### Post by smartboyathome on 2009-01-12
netcfg might work, along with iwconfig. Neither worked for me though (Intel 4965). Check out the wiki for Wireless.

---

### Post by Mr.Macdonald on 2009-01-12
nfg is a GUI, I need command line

---

### Post by kerry_s on 2009-01-13
> **Mr.Macdonald said:**
> nfg is a GUI, I need command line

? did you mean "netcfg", it's not gui.

instructions are here:
[http://wiki.archlinux.org/index.php/Network_Profiles](http://wiki.archlinux.org/index.php/Network_Profiles)

---

