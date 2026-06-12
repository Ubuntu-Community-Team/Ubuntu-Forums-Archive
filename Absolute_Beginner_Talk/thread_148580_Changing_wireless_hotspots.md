---
title: "Changing wireless hotspots"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by conbrio on 2006-03-22
Is there a way to automaticaly change from my home network to my school ntwork and vice versa upon boot up? Or is there an easier way to change the network profile without going to 'system-admin-networking' route. Thanks

ConBrio

---

### Post by Super King on 2006-03-22
I use Network-manager (install in Synaptic, or sudo apt-get install network-manager from the command line). Once it's installed I just added "nm-applet" into the Startup list (System->Prefs->Sessions->Startup programs) so it loads on startup and picks the correct wireless network.

---

### Post by conbrio on 2006-03-22
thanks for the reply. I have done what you said and I will know tomorrow if it works correctly or not. Thanks again

ConBrio

---

### Post by phen on 2006-03-22
another nice tool is wifi-radar. you can install it by synaptic (search for wifi-radar), oder by typing

sudo apt-get install wifi-radar

afterwards, you have to start the graphical interface and choose your network, enter wep key etc etc. save the profile. do the same at school. now, wifi-radar chooses the right network upon boot!

---

