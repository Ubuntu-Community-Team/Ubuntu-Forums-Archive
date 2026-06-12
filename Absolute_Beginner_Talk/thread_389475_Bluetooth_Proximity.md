---
title: "Bluetooth Proximity"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-03-20
I am looking to set up my computer to log me out when my blue tooth phone is out of range.   So when I walk away from my computer, it will automatically log me out, or at least go to a screensaver that requires a password.   I see that there are some Win32 apps for this but not for Ubuntu. 

Anybody have some help.

---

### Post by kidders on 2007-03-21
Hi there,

Doing things like this with Linux is pretty trivial, which may be why you're having trouble finding an app to do it. A quick shell script based around the output of **hcitool** ought to do the trick.

For example, **hcitool rssi 00:11:22:33:44:55** will give you the signal strength of a connection to a bluetooth device.

---

### Post by dexae on 2007-03-21
[http://www.open-gnss.org/cgi-bin/hg](http://www.open-gnss.org/cgi-bin/hg)

---

### Post by salsa_fcis_is on 2008-06-26
hi I'm also making bluetooth application using C programming.
I need to get the RSSI of mobile connected to my bluetooth 
Does anyone have any materials or code examples that I can use?
that would be great help thanks.

best regards,

salsa

---

