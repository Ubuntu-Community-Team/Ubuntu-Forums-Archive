---
title: "Can't get wireless internet running"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Rensole on 2007-05-31
ok I finally got ubuntu installed and running fine on my hp pavillion notebook (latop of course) but i cant seem to get my wireless internet to work. i have dsl directly connected to my home desktop computer, its a 2wire homeportal 1700HW.

---

### Post by khardbored on 2007-05-31
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by silentjudas on 2007-05-31
ok how does he do this?

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

we arent able to move anything into etc, and the sudo mv command is too confusing to figure out


HELLLLPPP!


*btw i am a friend of his, i'm helpin him out*

we try this

sudo mv </home/rensole/Desktop/wpasupplicant> /etc/default/

and we get this

bash: /etc/default/: Is a directory

---

### Post by kernel tom on 2007-05-31
there's a few things to check here...

first off is that ur wireless device is enabled, go to Network Settings and see if there is a check mark next to it, you may need to know your exact network name to connect first time

secondly, if you have any other means of connecting to the internet, ie. wired, i would strongly suggest downloading something called wlassistant, which will help you select, configure, and connect to wireless networks...

what kind of wireless card do u have installed? also, you will only need a wpa supplicant file if ur network is wpa encrypted, if not there is no need to bother with one.

---

### Post by silentjudas on 2007-05-31
ok a few things. wlanassistant.

we have a .deb but it wont grab the dependencies and i aint gonna go through getting all those

also: it aint in add/remove..

and he doenst know what his card is...

---

### Post by silentjudas on 2007-05-31
bump for help

---

### Post by kernel tom on 2007-06-02
linux should recognize his card

go into Network Settings, then see if the wireless connection is enabled... you need to put in the exact name of ur network...

and i said wlassistant... not wlanassistant

---

