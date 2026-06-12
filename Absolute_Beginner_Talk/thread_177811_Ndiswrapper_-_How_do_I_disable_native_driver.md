---
title: "Ndiswrapper - How do I disable native driver"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-05-16
I just recently got my wifi working by using Ndiswrapper. But to get it to work after boot, I have kill the driver, start it back up again then configure DHCP again, and now the interface is labelled wlan1 instead of wlan0. I think that this is happening because the native driver loads at boot, and when I kill it and start again ndiswrapper then loads the correct driver. How can I fix this so that ndis and the correct driver load at boot up?

---

### Post by evilgold on 2006-05-16
what chipset are you using. And what native driver?

to remove a driver from ndiswrapper you type "ndiswrapper -e [drivername]"

to stop a linux driver from loading at startup add its name to the file /etc/modprobe.d/blacklist

---

### Post by rubrboots on 2006-05-16
I am using a usb Netgear MA111, the module comes up as prism2_usb. I know how to stop and start the module. How do I find out the name of the two different drivers so I can add the native driver to the blacklist?

---

### Post by evilgold on 2006-05-16
[QUOTE=rubrboots]I am using a usb Netgear MA111, the module comes up as prism2_usb. I know how to stop and start the module. How do I find out the name of the two different drivers so I can add the native driver to the blacklist?[/QUOTE]

The drivers name is prism2_usb then. "blacklist prism2_usb"

why dont you want to use the native driver anyways? It would probably be a lot better then ndis... you'd be able to use kismet and stuff.

---

### Post by rubrboots on 2006-05-17
I would love to use the native driver, but after weeks of trying to get it to work I gave up. The ndiswrapper driver worked immediately but its a pain to have to stop and start it everytime I reboot. I did try to blacklist prism2_usb, but then ndis would not work either.

---

### Post by evilgold on 2006-05-17
try this
do everything as root (type sudo -s in a term)
blacklist ndiswrapper and unblacklist the prism2_usb (you can undo it later if this doesnt work)
```
gedit /etc/modprobe.d/blacklist

```
add the line
```
blacklist ndiswrapper
```
remove the line (if you have it
```
blacklist prism2_usb
```
save and go back to the terminal
then make sure ndiswrapper is stopped
```
rmmod ndiswrapper
```
start the native driver
```
modprobe prism2_usb
```
you may need to insall this package
(might need to use wired internet or download the package to a cd-r for this)
```
apt-get install linux-wlan-ng
```

Then you can try it out...
```
ifconfig prism2_usb up
iwconfig prism2_usb ESSID YOURESSID
dhclient
```
(if it still doesnt work, keep going)

to get it to auto start with your PC
edit /etc/network/interfaces to have this:( you might just edit the lines with prism2_usb or you may have to add them)
```

iface prism2_usb inet dhcp
auto prism2_usb
     wireless_mode managed
     wireless_essid YOUR-ROUTERS-ESSID
```

any other wlan interfaces, remove "auto" from them

reboot and see if its working...

If its still not working, reverse the steps, and remove auto prism2_usb from the interfaces file, remove ndiswrapper from the blacklist, readd prism2_usb to it. Long as you stop the prism2_usb from loading it shouldnt bother ndis.

---

