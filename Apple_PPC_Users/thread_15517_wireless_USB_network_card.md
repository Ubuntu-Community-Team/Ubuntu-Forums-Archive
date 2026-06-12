---
title: "wireless USB network card"
date: 2005-02-15
forum: Apple PPC Users
---

### Post by mac-mini-sweet-silence on 2005-02-15
Having bought a mac mini without the wireless network card, thinking I might use my existing USB dongle, I find out that it doesn't work. Well then, lets install linux. And all is good. Except that I have to fiddle around with the atmel wlan drivers, pathches and config files. Given enough time, I can probably get it to work.  :-P 

But I rather spend a small amount of cash to get a card that works out of the box with the 2.6 kernel. So, what card (or chipset) would you recommend?

---

### Post by pellix on 2005-02-22
I have a D-link dwl-122 and it works great, compiling wlan-ng drivers and installing linux-wlan-ng utilities :)

---

### Post by Pineault on 2005-02-22
This is a repost from another thread earlier on, I also have a D-Link DWL-122 USB Wifi (B) that works, used info from an earlier post on this list
[http://ubuntuforums.org/archive/index.php/t-5660.html](http://ubuntuforums.org/archive/index.php/t-5660.html)

one thing I haven't been able to do is to automate the lunch of the script during boot up, another major issue is the integration of the usb wifi in the various gnome interface network tools, any help on this would be appreciated,
and lately I've been suddenly loosing the connection and can't reastablish it.... very frustrating, have to plug in a wire...

---

### Post by ssam on 2005-03-17
basically this does not 'work out of the box'
you need to get the linux-wlan-ng drivers from synaptic, which requires an internet conection.
then make some scritps to start it, and edit a config file
then start the card manually.

does anyone know of a usb wireless NIC that just works?

---

### Post by skabber on 2005-03-17
[QUOTE=ssam]does anyone know of a usb wireless NIC that just works?[/QUOTE]

Apparently not.  In my [post](http://ubuntuforums.org/showthread.php?t=20449) a few days before this one, only one person mentioned that D-Link adapter, and apparently that doesn't work well, or out of the box, or with the gnome utilities.

---

### Post by cvalstad on 2005-03-20
Whats the possibility of wlan-ng being built in and making ubunt ready for wifi access out of the box?

I also have d-link usb dongle, and making it work is pretty damn hard. Well I am a linux newbie, but damn.

---

### Post by fdrake on 2007-08-22
hi there ,
  I plane to buy a wireless usb adapter card for my desktop, can anyone suggest me a good and compatible brand with ubuntu os. I was thinking to buy one of these three options:
    Delll wireless 1450 usb adapter
    GlobalFast  802.11g WIRELESS USB NETWORK CARD 
    NETGEAR 802.11G WIRELESS USB ADAPTER CARD 
Has any of you tried one of those before . Do they wiork well in Ubuntu? let me now please.
 thanks

---

### Post by stmiller on 2007-08-23
Note: This is an old thread. The DWL-122 should now work automatically, if people are still looking for a dongle.

Also if there are any usb adapters that have intel chipsets, those would probably be good. Intel wireless is generally well supported. Don't know if there are usb versions, though.

Also look for prism / orinoco chipsets.

---

### Post by fdrake on 2007-08-23
thank you stmiller , I'll keep your advise in mind when i order my wireless usb card. thanks

---

### Post by walter_f on 2007-08-24
> **stmiller said:**
> Note: This is an old thread. The DWL-122 should now work automatically, if people are still looking for a dongle.

Also if there are any usb adapters that have intel chipsets, those would probably be good. Intel wireless is generally well supported. Don't know if there are usb versions, though.

Also look for prism / orinoco chipsets.

Afaik, Feisty uses a kernel version already (2.6.20 or maybe .22) that supports the wireless chipsets by Ralink. The 802.11g chipset varieties by Ralink are the RT2500 and RT2501.

Find Linux-related docs and drivers (source code, just in case you want or need them) here:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

A good USB wireless stick based on the Ralink RT2500 is the WL-167G by Asus. The GN-WBKG by Gigabyte should also be mentioned.

There are many low-cost USB wireless sticks in the market based in the ZyDAS ZD1211 chipset, renamed to AR5007UG by Atheros. See a long list of ZyDAS-based sticks here:

[http://zydas.rapla.net/](http://zydas.rapla.net/)
[http://zd1211.wiki.sourceforge.net/](http://zd1211.wiki.sourceforge.net/)

Walter.

(Btw.: Using the appropriate drivers by Ralink, the WL-167G also works fine under Mac OS X).

---

### Post by gvigorus on 2007-09-20
> **walter_f said:**
> Afaik, Feisty uses a kernel version already (2.6.20 or maybe .22) that supports the wireless chipsets by Ralink. The 802.11g chipset varieties by Ralink are the RT2500 and RT2501.

Find Linux-related docs and drivers (source code, just in case you want or need them) here:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

A good USB wireless stick based on the Ralink RT2500 is the WL-167G by Asus. The GN-WBKG by Gigabyte should also be mentioned.

There are many low-cost USB wireless sticks in the market based in the ZyDAS ZD1211 chipset, renamed to AR5007UG by Atheros. See a long list of ZyDAS-based sticks here:

[http://zydas.rapla.net/](http://zydas.rapla.net/)
[http://zd1211.wiki.sourceforge.net/](http://zd1211.wiki.sourceforge.net/)

Walter.

(Btw.: Using the appropriate drivers by Ralink, the WL-167G also works fine under Mac OS X).
And will something like WL-167G work on a PPC platform? I'm debating between dwl-122 and wl-167G the latter is G and if it works natively with linux PPC, it would be the ultimate winner!!! Thanks.

---

### Post by gvigorus on 2007-09-20
Also, i see that WL-167G is on USB 2 interface. I have Powerbook G3 with USB 1 I believe. will this still work in G mode?

---

