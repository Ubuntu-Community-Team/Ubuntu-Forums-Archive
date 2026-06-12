---
title: "Wifi help... Probably because I'm a newbie"
date: 2007-01-23
forum: Apple PPC Users
---

### Post by zalberico on 2007-01-23
I have read through many how tos about setting up wifi in ubuntu and here's where I get.
Step one: install the bcm43xx-fwcutter (Done)
Step Two: Download the following and extract it: wl_apasta.o
I can't get the extraction to work, I have the file sitting on my desktop, I think the code would be:
sudo bcm43xx-fwcutter -w /lib/firmware -/Desktop/wl_apasta.o

I'm sure someone can see my obvious mistake somewhere (I hope)
thanks in advance
zman


Also link for those looking for the how to: [http://doc.gwos.org/index.php/BroadcomWireless](http://doc.gwos.org/index.php/BroadcomWireless)

---

### Post by Uta on 2007-01-24
I believe you misspelled "wl_apsta.o"
you had "wl_apasta.o"

---

### Post by zalberico on 2007-01-28
thank you for catching my stupidity
that was it
now it works, but strangely not at my house, it works at my friends house.
both are unsecured networks(I live with no one around and my parents don't  listen when I say we should have WPA) but it still won't work at my house.  It can't be a range problem because I tried setting it up right next to the router.
-thanks

---

