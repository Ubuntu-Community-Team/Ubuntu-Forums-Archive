---
title: "Wireless network detector"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-10-27
Can anyone help me find a good wireless network detector/sniffer.

i travel with my laptop alot and like to connect to wireless hotspot and wireless access points in hotels/other peoples house, but i can not always find out their SSID.

so i need to find something to detect wirless networks.

could someone please help me find a good one a show me how to download/install it.

thank you

---

### Post by chuckyp on 2006-10-27
Well for just locating networks use the network-manager it should show all availible networks in the area.

---

### Post by kent41 on 2006-10-27
I am not sure if this is what you want but this will show what is close by.

```

sudo iwlist ath0 scan
```

---

### Post by Jamesbowden on 2006-10-27
I cant find it, can you help me out with that? i go to system >> administrtion >> Networking. and i have to enter the SSID of the wireless network manualy.

---

### Post by kent41 on 2006-10-27
> **Jamesbowden said:**
> I cant find it, can you help me out with that? i go to system >> administrtion >> Networking. and i have to enter the SSID of the wireless network manualy.

Iam sorry you need to use the terminal and type "sudo iwlist ath0 scan"
less the quotes

---

### Post by Jamesbowden on 2006-10-27
Thats that worked

expect i had to do,

"sudo iwlist ra0 scan"

---

