---
title: "ASUS K53E, Bluetooth Adapter not found"
date: 2012-06-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kskr on 2012-06-03
I have installed Ubuntu 12.04 64 bit os on my ASUS k53E. I  cannot get bluetooth to work, I see that it says "No Bluetooth Adapter  Found". I have an Atheros Bluetooth adapter, could you please help me  how to get this fixed.
  



Thanks, Sunny.

---

### Post by BartlebyFrogsnatcher on 2012-06-25
I have the same exact problem. Suxorz.

---

### Post by Gato Verde on 2012-09-09
I have the same problem on an Asus UL50V

---

### Post by jaithehulk on 2012-09-10
Is your problem with the bluetooth adapter not being found or unable to turn on/off?.
I have Asus K53SD and had bluetooth adapter problem... I then used the blueman plugin found in the Ubuntu repo and it started working.

---

### Post by alzet on 2012-10-24
> **kskr said:**
> I have installed Ubuntu 12.04 64 bit os on my ASUS k53E. I  cannot get bluetooth to work, I see that it says "No Bluetooth Adapter  Found". I have an Atheros Bluetooth adapter, could you please help me  how to get this fixed.
  



Thanks, Sunny.

Just in file /etc/modprobe.d/blacklist.conf remove line
blacklist asus_acpi
or place # in begin like that
#blacklist asus_acpi

After reload all will be work.

---

