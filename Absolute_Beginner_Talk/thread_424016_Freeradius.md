---
title: "Freeradius"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by rugby82 on 2007-04-26
PLEASE HELP ME!!!! I AM A STUDENT AND I MUST CONFIGURE A RADIUS SERVER FOR A EMULATION  OF 802.1x.................I HAVE A  "mini" router and 2 computer......i have install xsupplicant and freeradius but i don't now how this server could be setup!!!!!  help me!!!! (i use ubuntu 6.10)

---

### Post by joft on 2007-04-26
Want kind of 802.1X do want to setup? I've got some experience with EAP-TLS and EAP-PEAP. I use them for WLAN authentication.

Setting up freeradius is not that hard, except for EAP-TLS/PEAP to work, you have to rebuild the freeradius package, because Debian developers disabled OpenSSL usage and thus TLS/PEAP support is not available in Debian/Ubuntu packages.
After that it is just a matter of editing some lines in freeradius's "/etc/freeradius/eap.conf" and "clients.conf" and perhaps "users".
So, again, what do you want to do? Tell use more about your goals, then I might be able to tell you what you have to do.

---

### Post by rugby82 on 2007-04-27
ok...thank you......i have setup freeradius server (user,eap and client), i have configurate xsupplicant........i launch this comand:
```
wpa_supplicant  -c /home/wpa_supplicant.conf(that i have created) -D wired -d 7 -i eth0
```
in the second machine i launch freeradius server(debug):
```
freeradius -X
```

but the NAS don't route auth message!!!! nas is a router OPEN WRT!

---

### Post by rugby82 on 2007-04-27
the kind of authentication.....i don't know....i thing that i must use the most simple!!!!

---

### Post by joft on 2007-04-28
> **rugby82 said:**
> ok...thank you......i have setup freeradius server (user,eap and client), i have configurate xsupplicant........i launch this comand:
```
wpa_supplicant  -c /home/wpa_supplicant.conf(that i have created) -D wired -d 7 -i eth0
```

> **rugby82 said:**
> the kind of authentication.....i don't know....i thing that i must use the most simple!!!!

Well, show us your wpa_supplicant.conf (and perhaps your eap.conf of your freeradius server) - it should reveal the kind of authentication you want to use.

> **rugby82 said:**
> 
in the second machine i launch freeradius server(debug):
```
freeradius -X
```

but the NAS don't route auth message!!!! nas is a router OPEN WRT!

So you want to use 802.1X over _wired_ network connection, right?

Hmmm, I never tried OpenWRT's or in fact Linksys'/Broadcom's NAS with wired connections. ATM I am not sure about it, but did you check, that the nas daemon is called the right way? AFAIK you have to specify the interface where it listens .... so it has to be the wired one, not the wireless one of your WRT box ....

---

### Post by rugby82 on 2007-05-01
thank you very much....but...finally i have setup freeradius server and xsuplpicant (wpa supplicant)....now i must configur the NAS in EAP modes and i have finish for moment!!
i give you the simple setting of supplicant for help other people:

wpa_supplicant.conf ```
default {
  eap-md5 {
      username = <BEGIN_UNAME>giulio<END_UNAME>
      password = <BEGIN_PASS>giulio<END_PASS>
  }}

``` 
this is linux string for launch supplicant
```
 wpa_supplicant -D wired -i eth0 -c/(path of wpa_supplicant.conf) -d 7
```


freeradius need to set clients.conf, eap.conf, radiusd.conf!
thank you bye

---

