---
title: "Bluetooth and Nokia 6111"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by spnoe on 2007-05-25
I am trying to get my Nokia 6111 to sync with Evolution using Multisync. Using the options in Multisync I have managed to get the phone recognised but when I test connection, a message just says connection failed. I have loaded all the Bluetooth programmes/files that I could find in Synaptic and the Bluetooth manager now shows up on the taskbar.
I have also tried to send a file from the phone but that does not seem to work either.

Any help much appreciated

Thanks Steve

---

### Post by Inxsible on 2007-05-25
Can you show us the hcid.conf file?
```

sudo gedit /etc/bluetooth/hcid.conf

```
 
Also make sure you have installed *everything*
 
```

sudo aptitude install multisync bluez-gnome bluez-utils

```

---

