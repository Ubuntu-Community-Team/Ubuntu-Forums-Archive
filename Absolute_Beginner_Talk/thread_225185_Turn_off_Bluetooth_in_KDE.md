---
title: "Turn off Bluetooth in KDE"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-07-29
Since I have no wireless devices, I'd like to turn off Bluetooth and keep it from loading at boot. But when I try to access it in the KDE control centre I get:

DCOP derror when calling service () 

and when I get to the actual configuration windows, I have no idea what to do. The Enable Service button is greyed out.

When I click on Help, I get:
An error occurred while loading help:/kdebluetooth/components.html#components.kbluetoothd.configuration:
The process for the help protocol died unexpectedly.

I don't want to uninstall it (I live in hope I can afford fancy hardware one day) but how can I just disable it?

---

### Post by Footissimo on 2006-07-29
Have you tried the BUM (Boot-up manager) - its in the repos and allows you to activate / deactivate services via a nice GUI :)

---

### Post by editrix on 2006-07-29
Totally forgot about BUM. I've just downloaded it. Thanks for the suggestion.

---

### Post by editrix on 2006-07-30
BUM got rid of the bluetooth stuff, but kbluetoothd is still running--and eating up resources.

---

