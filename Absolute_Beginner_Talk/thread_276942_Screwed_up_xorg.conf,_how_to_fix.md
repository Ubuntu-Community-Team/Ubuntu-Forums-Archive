---
title: "Screwed up xorg.conf, how to fix ??"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-10-13
Hey I was messing around with the xorg.conf file and changed my 'Device' driver from "fglrx" to "ati". I wanted to test different settings just for the heck of it. Turns out now I cant even boot kubuntu (im using KDE). Right now im in my live cd. I tried mounting my hdd (which only has kubuntu on it) but it says 'please check if the device is connected properly' and wont mount. 

How can I get to my xorg.conf file in the terminal on the live cd to fix this problem?:confused:

EDIT: will the usual ```
 sudo kate /etc/X11/xorg.conf 
``` do the trick or do i have to get into the hdd first?

---

### Post by PriceChild on 2006-10-13
Boot up your system without the live cd.

when it informs you x has crashed, press ctrl+alt+f1 to get to tty1

log in, then
```
sudo nano /etc/X11/xorg.conf
```
and change it back to fglrx
ctrl+x then 'y' and enter to save
```
sudo /etc/init.d/kdm restart
```
And all should work.

---

### Post by WalmartSniperLX on 2006-10-13
> **PriceChild said:**
> Boot up your system without the live cd.

when it informs you x has crashed, press ctrl+alt+f1 to get to tty1

log in, then
```
sudo nano /etc/X11/xorg.conf
```
and change it back to fglrx
ctrl+x then 'y' and enter to save
```
sudo /etc/init.d/kdm restart
```
And all should work.


Ok thank you very much :D

---

### Post by PriceChild on 2006-10-13
Let us know how it goes... thank me when its working ;)

---

### Post by WalmartSniperLX on 2006-10-13
Thanks again :D Its fixed. Im logged in, and everything is fine :D :D

---

