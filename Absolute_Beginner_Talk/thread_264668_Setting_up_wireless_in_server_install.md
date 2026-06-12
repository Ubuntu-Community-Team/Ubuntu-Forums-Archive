---
title: "Setting up wireless in server install"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by k94382 on 2006-09-25
I have installed the server edition on my laptop and I plan on installing fluxbox on the laptop. First though, I would like to get my wireless card working. What would be the best way to achieve this without having internet as my only access will be WPA secured wireless internet. Any recommendations?

---

### Post by dmizer on 2006-09-25
there are plenty of howto's for wireless adapters, so a good start would be letting us know what card you have.  you might try some searches on this site for howto's on your card.

it might also help to know the chipset of your card.  so with the card inserted, post the output of lspci, and that should give us the chipset.

---

### Post by k94382 on 2006-09-25
I use a PCMCIA card which is the linksys WPC54G.

---

### Post by dmizer on 2006-09-25
what version number?

---

### Post by k94382 on 2006-09-25
v3

---

### Post by dmizer on 2006-09-25
try here: [http://www.ubuntuforums.org/showthread.php?t=190967&highlight=howto+wpc54g+v3](http://www.ubuntuforums.org/showthread.php?t=190967&highlight=howto+wpc54g+v3)

---

### Post by k94382 on 2006-09-25
For that howto, don't you need internet to update the repositories? Also, in CLI, would I type "sudo aptitude?"

---

### Post by dmizer on 2006-09-25
yes you will need internet for that howto.  have you inserted the card to see if it actually functions?  from the looks of that howto, the card may very well be supported natively now.

for future reference aptitude and apt-get are perform the same basic function.  aptitude just does a better job of it.  so if you see apt-get in a howto, just replace it with aptitude and you'll do fine.  most people are still hanging on to apt-get out of habit.

1) insert your card
2) edit networking and add wlan0:
```
sudo nano /etc/network/interfaces
```
at the end, insert:
```
iface wlan0 inet dhcp
```
3) do the following:
```
sudo iwlist wlan0 scan
```

this will not give you wpa (i don't know how to configure it as i don't have it), but it will let you know if your card is at least functioning.  then we can go from there.

---

### Post by k94382 on 2006-09-25
In the end I get a message that says that the device is not capable of scanning. So what's the next step??

---

