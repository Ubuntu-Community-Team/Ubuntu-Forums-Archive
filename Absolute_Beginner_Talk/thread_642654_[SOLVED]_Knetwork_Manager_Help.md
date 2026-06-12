---
title: "[SOLVED] Knetwork Manager Help"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-12-16
Hi,

My current wifi connection is secured. So when I clicked on the network it asked me for the key. I entered the key but it wouldnt proceed to connect to the network. After several attempts, I tried the manual connection and set the default gateway, ssid and key etc. and it connected without any trouble. My question is why it had trouble connecting automatically even when I entered the key? Secondly, when I right click on KNetwork it doesnt display all the networks in the neghibourhood. I believe this is because I selected a manual configuration. How do I get it back to the automatic configuaration.

Thanks

---

### Post by linuxnovice on 2007-12-17
Could someone please help?

---

### Post by linuxnovice on 2007-12-18
I figured it out myself.
If someone else need help on this...

You need to edit the /etc/network/interfaces file and comment out these:
#iface eth1 inet dhcp
#wireless-essid "network-id" (without quotes)
#wireless-key "key" (without quotes)

You also need to add auto eth1 before these lines. (Assuming eth1 is your wireless interface..)

---

