---
title: "Tips on working USB wifi on Powerbook G4 12&quot;?"
date: 2005-02-17
forum: Apple PPC Users
---

### Post by paer on 2005-02-17
Hi!

I have given up on searching for ways to get Airport Express to work on Ubuntu @ Powerbook G4 (there seems to be no way). Instead I have decided to spend some money on a USB Wifi adapter.

Now I would like to hear from other Ubuntu @ Powerbook users that have a working USB wlan (802.11b or 802.11g) adapter:

- what adapter do you use (brand, chipset)?
- did you have to do anything special to make it work?
- if your setup differs from mine, please tell me. I have a Powerbook G4 867MHz with 12" screen.

Thanks in advance.

---

### Post by danderso on 2005-02-19
Yeah, I would also like to know if someone could reccomend a wireless usb card that would work w/ a 12" powerbook.

---

### Post by ewaldgroup on 2005-02-19
Ditto

- ewaldgroup

---

### Post by Pineault on 2005-02-21
I have a D-Link DWL-122 USB Wifi (B) that works, used info from an earlier post on this list
[http://ubuntuforums.org/archive/index.php/t-5660.html](http://ubuntuforums.org/archive/index.php/t-5660.html)

one thing I haven't been able to do is to automate the lunch of the script during boot up, another major issue is the integration of the usb wifi in the various gnome interface network tools, nay help on this would be appreciated

---

### Post by chascon on 2005-02-26
Does the  D-Link DWL-122 USB Wifi (B) also work with Panther too?  How?  Well?  I read that you can hack these things but sometimes they result in kerne panics inOS X.  ... Not that I want to keep using OS X extensively but I would like to be able to throw out broadcom's shitty airport extreme if I could use a usb wifi with free source drivers at least with ubuntu and perhaps perhaps binary drivers with OS X, although I would like  free source drivers for both OSs.  The point is that I want a wireless tht will work with both systems.

Any advice? Leads, links?

---

### Post by ssam on 2005-02-27
i think it does work in panther, although i havve not tried it.

it can be a pain to get working in ubuntu though. it uses the linux-wlan-ng drivers, which are not included by default and don't work with the standard ubuntu networktools. you have to use synaptic to get the drivers (so you need another source of network) and then use a script to connect. also it can be a bit flakey and loose conection.

i imahine with a few requests linux-wlan-ng could be moved into the main distro and then it might work fine.

ssam

---

