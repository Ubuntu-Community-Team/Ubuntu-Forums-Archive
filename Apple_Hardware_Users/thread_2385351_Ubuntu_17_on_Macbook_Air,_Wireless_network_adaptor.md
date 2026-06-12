---
title: "Ubuntu 17 on Macbook Air, Wireless network adaptor is recognized but no wifi"
date: 2018-02-19
forum: Apple Hardware Users
---

### Post by ababaei2000 on 2018-02-19
Hey Guys,

Im quite new in Ubuntu. I installed Ubuntu on my system, by running ```
 lshw -c network
``` the network adapter is appeared. but still there is no Wifi, I also went through  "Software & update->additional Drivers-> using broadcom 802.11" and it didnt work as well. I have no internet or ethernet on this laptop.Can anyone help me?

---

### Post by Hadaka on 2018-02-19
Hi, please post he output of..
```
lspci -n | awk '/0200|0280/{print$3}'
```
*If this is a usb wifi then post the output of..
```
lsusb | grep -v Linux
```
Thanks

---

### Post by perillons on 2018-02-19
[COLOR=#333333][FONT=monospace]# fix it[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]edit the /etc/NetworkManager/NetworkManager.conf file[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]And add:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][device]
wifi.scan-rand-mac-address=no

Example:NetworkManager.conf


[/FONT][/COLOR][main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no
[COLOR=#333333][FONT=monospace]
[/FONT][/COLOR]

---

### Post by QIII on 2018-02-19
Moved to Apple Hardware Users

---

### Post by newhacker1746 on 2018-02-19
Post[FONT=courier new] lspci -nnk[/FONT] output.

---

### Post by ababaei2000 on 2018-02-20
Hi
The output is:
14e4:430a0

---

### Post by ababaei2000 on 2018-02-20
[COLOR=#000000]Hi[/COLOR]
[COLOR=#000000]The output is:[/COLOR]
[COLOR=#000000]14e4:430a0[/COLOR]
> **perillons said:**
> [COLOR=#333333][FONT=monospace]# fix it[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]edit the /etc/NetworkManager/NetworkManager.conf file[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]And add:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][device]
wifi.scan-rand-mac-address=no

Example:NetworkManager.conf


[/FONT][/COLOR][main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no
[COLOR=#333333][FONT=monospace]
[/FONT][/COLOR]

---

### Post by ababaei2000 on 2018-02-20
[COLOR=#000000]Hi[/COLOR]
[COLOR=#000000]The output is:[/COLOR]
[COLOR=#000000]14e4:430a0[/COLOR][

QUOTE=Hadaka;13741336]Hi, please post he output of..
```
lspci -n | awk '/0200|0280/{print$3}'
```
*If this is a usb wifi then post the output of..
```
lsusb | grep -v Linux
```
Thanks[/QUOTE]

---

### Post by ababaei2000 on 2018-02-20
I test this procedure before. It didnt work
> **perillons said:**
> [COLOR=#333333][FONT=monospace]# fix it[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]edit the /etc/NetworkManager/NetworkManager.conf file[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]And add:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace][device]
wifi.scan-rand-mac-address=no

Example:NetworkManager.conf


[/FONT][/COLOR][main]
plugins=ifupdown,keyfile


[ifupdown]
managed=false


[device]
wifi.scan-rand-mac-address=no
[COLOR=#333333][FONT=monospace]
[/FONT][/COLOR]

---

