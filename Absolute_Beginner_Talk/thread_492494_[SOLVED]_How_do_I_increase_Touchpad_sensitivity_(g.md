---
title: "[SOLVED] How do I increase Touchpad sensitivity (gysnaptics maxed out)"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-07-04
I installed gysnaptics which helped a little, but even after increasing sensitivity to max it's not enough.  How do I increase it further?

---

### Post by AncientPC on 2007-07-04
Nevermind, I found the answer in this thread:
[http://ubuntuforums.org/showthread.php?t=133796&highlight=dell+inspiron+laptop+touchpad+sensitivity](http://ubuntuforums.org/showthread.php?t=133796&highlight=dell+inspiron+laptop+touchpad+sensitivity)

Specifically:
[quote="Andrewski"]
As mentioned on Launchpad ([https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/28648](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/28648)), try adding the following to your Synaptics section:

```
Option "MinSpeed" "1.0"
Option "MaxSpeed" "1.0"
Option "AccelFactor" "0.3"
```[/quote]

---

