---
title: "WPA problems"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Bdubbya on 2006-07-30
I got my wireless working on a hijacked network without any security.

Now i need to get on my network. I use WPA security on my sonicwall with wireless. 

All the options in the bulit in network app are HEX and plaintext.

Is there support for WPA?

---

### Post by Bdubbya on 2006-07-30
I had to use NDISwrapper to get the driver going if that make a diffrence.

---

### Post by Apple 101 on 2006-07-31
Install the packages *wpa_supplicant*, *ndisgtk*, *wireless-tools*, *wpa_gui*.  You will also need to enable the Universe repository in Synaptic.

Open a terminal and type: *sudo wpa_gui*.

---

