---
title: "is there a way to use windows wireless card drivers?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2006-08-26
^^^^^^

---

### Post by Bachstelze on 2006-08-26
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by The_Artist on 2006-08-26
Some windows drivers works perfectly with ndiswrapper. But if it's not indicated, don't loose too much time trying to install them.

Either buy a ralink or an atheros chipset based card, installed in 30 s !

---

### Post by L_o_N_e_R on 2006-08-26
my wireless card was listed and downloaded the drivers

im using the graphical installer and it doesnt show any sign thats installed

what am i doing wrong?

---

### Post by The_Artist on 2006-08-28
I can't help a lot because i don't know very much ndiswrapper but are you sure of the version of your downloaded driver ? It must me EXACTLY the same than mentionned in the ndiswrapper instructions...

---

### Post by L_o_N_e_R on 2006-08-28
it is the same model i found in the list...... omg.....


heres my card

Card: D-Link DWL-G630, rev C

    * Chipset: Atheros
    * pciid: 168c:001a
    * Driver: [ftp://ftp.dlink.com/Wireless/dwlg630_revC/Drivers/dwlg630_driver_300.zip](ftp://ftp.dlink.com/Wireless/dwlg630_revC/Drivers/dwlg630_driver_300.zip)
    * Other: Works with WEP and WPA with TKIP cipher. ndiswrapper 1.1 compiled from source using Debian testing kernel 2.4.27-2.

---

### Post by Dr. Nick on 2006-08-28
have you gone through system - administration - networking and configured it yet? does the wireless even show up in the network control panel?

run this command from a terminal and post back  the results

**lsmod**

that will show you all hardware drivers loaded

---

