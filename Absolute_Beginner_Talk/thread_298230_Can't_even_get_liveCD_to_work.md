---
title: "Can't even get liveCD to work"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2006-11-12
I have been using vmware and playing around with ubuntu and I've been pretty happy so far. I was going to install the operating system, but the liveCD doesn't work even though it works in vmware.

I have an HTPC (home theatre PC) that I've been using with windows XP as a PVR and I wanted to give ubuntu a try with mythtv.   Well my PC is connected to a television with composite cable and ubuntu will boot up with the CD, but after the status bar is gone I cannot view anything.  My television only plays the sound that ubuntu is booting up, but I can't view anything.

Any suggestions?

---

### Post by Ecthelion on 2006-11-12
Maybe you should try to download the alternate version and install it...
This isn't with life cd, but with the old install guide.

You can find this alternate version[ here ]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download") (click on toher installation options of a nearby mirror and then scroll down to alternate cd install and download the appropriate iso)

---

### Post by bone2006 on 2006-11-12
Thanks for the response
I want to make sure I understand, the alternative CD is the same as the standard CD except it doesn't have a GUI for installation and it's not a live CD?

I actually wanted to try out the liveCD to make sure my internet connection worked, before switching over from windows.  Using vmware it's bridging the internet connection, so I can't really verify that my usb wifi connection will work with ubuntu.

Thanks again

---

### Post by Ecthelion on 2006-11-12
> Thanks for the response
I want to make sure I understand, the alternative CD is the same as the standard CD except it doesn't have a GUI for installation and it's not a live CD?

Not really...
The alternative cd contains a version of [Xubuntu]("http://www.xubuntu.org/"),
which is
[QUOTE=www.xubuntu.org]Xubuntu, pronounced as Zooboontoo, is a complete GNU/Linux based operating system with an Ubuntu base. It is lighter on system requirements and tends to be more efficient than Ubuntu with GNOME or KDE, since it uses the Xfce Desktop environment, which makes it ideal for old or low-end machines, thin-client networks, or for those who would like to get more performance out of their hardware.[/QUOTE]

But since the installation is non-graph you should have no problems installing it. Once it is installed you can use the command-line to (if it is still necessary) to make the changes to your xorg.conf, which is the file that (I think) is causing trouble.

You can always start with a dual-boot Windows / Linux if you are unsure your usb wifi is going to work and you can't do it without.
If it turns out that it does work after installing, then you can delete windows.
If it doesn't work you'll have to ask for help, and in meanwhil you can use windows to for your usb-wifi...

---

