---
title: "Asus &amp; fiesty not getting along, no internet"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2007-04-10
My Asus is not happy with (x)ubuntu. When I boot the xubuntu feisty live CD these lines, which look like trouble to my novice eyes, come up:
> 
init:/etc/event.d/tty6:15: unknown stanza

I think I got that right, it repeats itself about 6 times. 

next there's> 
*starting kernel event manager...
 udevd[5093]: lookup_group: specified group "nvram" unknown

then later> 

Loading hardware drivers...
udevd-event [5143]: udev_db_add_device: unable to create db file 
'/dev/.udev/db/class@input@mice':no such file or directory
[  63.16800] intel-rng: FWH not detected
[  64.172000] sdhi:slot0: Controller reports >25MHz base clock, but no high speed support.
udevd-event[6896]: udev_db_add_device: unable to create db file '/dev/:udev/db/c
lass@input@input0@mouse0': No such file or directory

there's also 
> 
*Activating swap...
mount: function not implemented

which I guess is ok, but soon:
> 
*setting up console font and keymap...
cat: /var/lib/acpi-support/system-manufacturer: no such file or directory
cat: /var/lib/acpi-support/system-product-name: no such file or directory
cat: /var/lib/acpi-support/systemversion: no such file or directory
cat: /var/lib/acpi-support/bios-version: no such file or directory

the exact details seem to vary per boot for, to me, no apparent reason. 

In xubuntu feisty there comes a graphic message about unsupport driver. the details are:
Intel pro/wireless 3945 network conection driver for linux, enabled & in use.

I cannot get online wired or not through my router. I can get on wireless with no setup on vista or with no setup for wired connection with xubuntu 6.10 on my late toshiba. 

I went to network settings. wired is checked & enabled, auto dhcp.
wireless could be enabled if i gave it a spurious name. there's no wep, & it says autp dhcp.

still mozilla & gaim don't bother trying to connect

I don't know what's significant there. hopefully something. 

This is an Asus U5F. its my first look at vista, in chinese which I can't understand. you can imagine how much fun i'm having. me want english xubuntu. ubuntu 6.10 livecd can't connect to the internet either. I guess there's just no lan driver for me. noooooooooo

why god, why? whyyyy... (beating tear-stained desk with fist)

---

### Post by 00arthuryu on 2007-04-10
same problem :( i just went the easy way out and put a network card in lol

---

### Post by flixer on 2007-04-10
Feisty is coming out real soon. There's a big chance that your laptop will work with it.
[https://wiki.ubuntu.com/FeistyReleaseSchedule](https://wiki.ubuntu.com/FeistyReleaseSchedule)

---

### Post by leetrefz on 2007-04-10
ok I'll wait but if it doesn't work then I'm going back on the bottle.

---

### Post by darwin_te on 2007-05-27
Kubuntu 7.04 (Feisty)
ASUS G1

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

WEP 104-bit (128-bit) setting connecting to Windows AP:

/etc/network/interfaces:

########################
#home - wifi
########################

auto eth1
iface eth1 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid youressidhere

# passphrase is test
# see [http://www.powerdog.com/wepkey.cgi](http://www.powerdog.com/wepkey.cgi) (Passphrase To Hexadecimal WEP Keys)
wireless-key1 9FDF3BFDFB10AFEB0925EF9605

wireless-defaultkey 1
wireless-keymode open

command line to bring wireless network up:

>ifup eth1

---

