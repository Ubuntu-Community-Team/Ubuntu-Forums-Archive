---
title: "Canviar mode Bluetooth de HCI a HID"
date: 2015-08-26
forum: Catalan Team
---

### Post by Automat2 on 2015-08-26
Vull canviar el mode d'us del meu Bluetooth de HCI a HID. Uso un teclat i mouse Logitech amb un adaptador CSR perquè l'adaptador Logitech m'ha deixat de funcionar. 

Aquest adaptador es pot fer servir en els dos modes HCI/HID en principi però no se la manera de canviar-los.

Abans hi havia un command de BlueZ que es veu que funcionava -hci2hid-, però a Vivid ja no hi es entre la llista segons el Software Centre. 

He trobat per internet solucions antigues com aquí  [URL="https://help.ubuntu.com/community/BluetoothSetup"]https://help.ubuntu.com/community/BluetoothSetup
[/URL]
però no tinc l'arxiu /etc/default/bluetooth sinó /lib/udev/rules.d/97-bluetooth-hid2hci.rules

Hi ha algú que sàpiga com fer que l'adaptador CSR passi de mode HCI a HID?

Gracies.

---

### Post by wgarcia on 2015-08-31
No tinc coneixement sobre el problema que comentes, però mira si aquesta solució pot funcionar:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/444420](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/444420)

És molt antiga però, i possiblement ja la tinguis registrada.

---

### Post by Automat2 on 2015-08-31
Gracies [**[COLOR=#339900][B]wgarcia**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=242060")

Em sembla que ja havia vist aquesta solució. Ja havia provat de canviar l'argument que hi ha en una de les solucions en el fil, i encara he canviat l'adreça del dispositiu, però encara no em funciona.

:(

---

