---
title: "bluetooth stopped after issuing restart"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by orangemoose on 2008-04-15
Ok, back again with BT issues.

I read the tutorials I was referred to.

I understood that 

sudo /etc/init.d/bluetooth start 

would restart BT.

Instead, I cant get BT even after reboot.

I fixed this last time with a reinstall, but that seems drastic to do every time the mouse stops working.

I need to know if bluetooth or bluez-utils is the correct module.

I have done sudo apt-get install bluez-utils.

Any help appreciated.

---

### Post by Inxsible on 2008-04-15
Try this```
sudo hcitool scan
``` to see if it see bt devices around your machine. If it does, then BT should be up and running.

---

### Post by orangemoose on 2008-04-15
thanks for the tip.

it just times out though.

and the add device button on the BT interface doesn't find anything either.

---

### Post by Inxsible on 2008-04-15
Ok is this a laptop?

Do you have a switch that enables disables Bluetooth? Maybe that's in the off position

---

