---
title: "Presario V2000 Internal WIFI Card"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by shogaashi on 2007-08-07
Hi

I have a Compaq Presario V2000 which I just installed Ubuntu V 7.04 on. Works great but cannot get the internal WIFI card to work. Cannot establish a wireless connection and the little blue light on the Laptop (illuminated means wireless card is on) does not light up.

Anyone have any suggestions or had this problem before?

I am very very new to all of this

Thanks

---

### Post by misfitpierce on 2007-08-07
V2000 usually have broadcom cards. Try this in terminal

sudo apt-get install bcm43xx-fwcutter

Click yes when it asks to extract firmware... within a few moments or after reboot the light should come on and you should be set to go.

---

