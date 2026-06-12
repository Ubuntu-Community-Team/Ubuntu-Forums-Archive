---
title: "Cannot log on to WPA wireless network"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by oxo2oxo on 2007-11-02
Have just installed 7.10 and delighted to have WPA support, however I can see the wireless network and the dialogue box opens to enter password but the 'log onto network' button stays grayed out

---

### Post by plinydogg on 2007-11-02
I also have a WPA protected network. I use WICD instead of the default program (Network Manager) because the latter wouldn't let me log into my network...

---

### Post by oxo2oxo on 2007-11-02
Excuse WICD ?

---

### Post by rudeboyskunk on 2007-11-02
I assume you both have wireless cards that support WPA.

You need to install wpa supplicant.  Open up Synaptic and just do a search for "wpa."  You'll find it.

---

### Post by plinydogg on 2007-11-02
I just use WICD...much better than the Network Manager + WPASupplicant IMHO...

---

### Post by oxo2oxo on 2007-11-02
I believe in7.10 wpa supplicant is installed already. Can you tell me what this WICD is ?

---

### Post by oxo2oxo on 2007-11-06
OK, found WICD installed and works fine. Not sure what the problem is with Network Manager
Many thanks

---

### Post by swoll1980 on 2007-11-06
if your using ndiwrapper sometimes wpa will not work even if the card supports it. This is what happend to me. I just switched to 128bit wep and haven't had any problems.
wep 128bit should be ok unless you have a hacker living next door to you.

---

