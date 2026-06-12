---
title: "is there a way???"
date: 2008-09-12
forum: Apple Hardware Users
---

### Post by imacbo on 2008-09-12
Hi I have a 700mhz ibook running OSX 10.2.8 and my cd drive will not read any cds. Is there anyway to install linux on this computer? I need a cheap way to do this because the computer was free and I dont want to put money in an old computer. Thanks

---

### Post by lildeb on 2008-09-12
I don't know if you can do Ubuntu, but I would say try putting DamnSmall on a flash drive.

---

### Post by johnidi on 2008-09-12
Yes there is a way!
[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html")

---

### Post by Nopposan on 2008-09-12
Yes, there is.

However, you'll probably need a working CD-ROM to install it and I hope there's nothing mechanically wrong with your iBook that's preventing the CD-ROM from working.

I assume that your iBook is a G3 and has powerpc architecture.

I understand the easiest way is to buy Yellowdog Linux and install it, but I haven't tried it myself.  Ubuntu 8.04 does not come in a Powerpc version, but Ubuntu is basically Debian Testing with a little added artistic flair, some Gnome desktop tweaks, and some generic user-friendliness and hand-holding thrown in.  Ubuntu 7.10 does have a Powerpc version and you can find that somewhere if you really want to have an outdated version of Ubuntu.

So, Debian Testing does come in a Powerpc version!  Also, it's not really much more difficult to install than Ubuntu, although getting all the features on your laptop working approximately as it did under OSX will take you some time and effort regardless of which distro you choose. 

You can download the Debian Testing for Powerpc at the following location:
[http://www.debian.org/devel/debian-installer/]("http://www.debian.org/devel/debian-installer/")
I recommend downloading the net install CD and booting from CD-ROM while your computer is connected by ethernet to your internet router or modem.  You'll need to hold down the "C" key to boot from CD-ROM or DVD-ROM, I think.

You can find additional information about installing Debian on an iBook here:
[http://lowendmac.com/ed/packer/08jp/debian-linux-ppc-mac.html]("http://lowendmac.com/ed/packer/08jp/debian-linux-ppc-mac.html")
And, you can use the following forum for help with that:
[http://forums.debian.net]("http://forums.debian.net")

Then, if you liked the look of OSX, you can even customize your desktop to look more like it.  Just Google for "making Linux look like OSX" or some other such search.

P.S.  If time equals money, how come zero dollars equal an indefinite number of hours?

:)

Cheers.

---

### Post by snowpine on 2008-09-12
> **Nopposan said:**
> Ubuntu 8.04 does not come in a Powerpc version, but Ubuntu is basically Debian Testing with a little added artistic flair, some Gnome desktop tweaks, and some generic user-friendliness and hand-holding thrown in.  Ubuntu 7.10 does have a Powerpc version and you can find that somewhere if you really want to have an outdated version of Ubuntu.


You can find the PowerPC version of Ubuntu 8.04 here: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

I agree that Debian is cool, too. :)

---

### Post by gaussian on 2008-09-12
> **Nopposan said:**
> Yes, there is.

However, you'll probably need a working CD-ROM to install it and I hope there's nothing mechanically wrong with your iBook that's preventing the CD-ROM from working.

I assume that your iBook is a G3 and has powerpc architecture.

I understand the easiest way is to buy Yellowdog Linux and install it, but I haven't tried it myself.  Ubuntu 8.04 does not come in a Powerpc version, but Ubuntu is basically Debian Testing with a little added artistic flair, some Gnome desktop tweaks, and some generic user-friendliness and hand-holding thrown in.  Ubuntu 7.10 does have a Powerpc version and you can find that somewhere if you really want to have an outdated version of Ubuntu.

Cheers.

Ubuntu 8.04 does come in (community supported) form for PPC. Just look at the Sticky on this forum. What is true that many people (including me) had hard time installing 8.04 from Live-CD, I went on my Powerbook G3 (Pismo/Firewire) the route of installing 7.04 and upgrading to 7.10 and 8.04. Works perfectly here.

As for the specific OP question of installing without CD: there should be a way of doing this with USB stick. However, most of the advice out there is "PC specific" (including stuff cited in this thread). I tried this (I found a Gentoo howto that could be applied to Ubuntu), but could not make it work. OP should search for "USB linux install PPC" or something like that. Booting the machine is very different under PPC than under Intel. In my case what prevented me from doing this was the Openfirmware did not see the USB stick. Your mileage may vary.

---

### Post by Nopposan on 2008-09-14
Thanks.  I really didn't know about the Ubuntu 8.04 for PowerPC.  It's good to have options.

Cheers.

BTW, I would recommend a lightweight desktop like LXDE, Fluxbox, or maybe Xfce.  I installed Debian Testing with Xfce on an iMac G3 and it's pretty nice; I think maybe LXDE or Fluxbox would have been better choices for the sake of responsiveness/speed though.  Also, you'd better choose the alternative installer and not run a desktop from the live CD; it'll be too slow unless the desktop is something really lightweight like Fluxbox.

---

