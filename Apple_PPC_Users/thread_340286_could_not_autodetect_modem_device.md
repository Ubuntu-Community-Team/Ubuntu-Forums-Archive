---
title: "could not autodetect modem device"
date: 2007-01-17
forum: Apple PPC Users
---

### Post by linuxppcuser on 2007-01-17
Hi
I am trying to get my internal modem to work on my iMac
I am wanting to use it to send and receive fax
I have tried under system/administration/networking 
it could not autodetect modem device

Linuxppcuser

---

### Post by ssam on 2007-01-17
have you tried with gnome-ppp

it is in the repos so you can install it with synaptic if you have an alternative internet connection. if not you can download ubuntu packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install them by copying them into your linux home folder and double clicking them. the gnome-ppp package page ( [http://packages.ubuntu.com/edgy/net/gnome-ppp](http://packages.ubuntu.com/edgy/net/gnome-ppp) ) also lists the dependancies of gnome-ppp. i think all of them are installed by default, but if you get error messages about missing dependacies then you will need to download and install those first.

---

### Post by linuxppcuser on 2007-01-17
I do have broadband connection I have installed gnome-ppp
but it still did not detect the internal modem
I have looked at Device Manager and it does not show any modem
I have efax-gtk installed but it did not detect the internal modem either.

linuxppcuser

---

### Post by ssam on 2007-01-17
are you sure there is a modem in there?

one posiblilty is that it is a software modem. they generally dont work with linux. [http://en.wikipedia.org/wiki/Software_modem](http://en.wikipedia.org/wiki/Software_modem)

---

### Post by linuxppcuser on 2007-01-17
I had Kubuntu 5.04 PPC installed and the internal modem worked find 
I had know problem autodetect the modem then, for dial-up,
until now since I upgrade to Dapper and want to use the internal modem
and I can't.

linuxppcuser

---

