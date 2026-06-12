---
title: "getting the synaptics touchpad driver."
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by ataranea on 2007-02-13
i d/l the driver for the synaptics touchpad but its a  .tar.gz file and i have no idea how to use that.

---

### Post by unisol on 2007-02-13
Have you tried installing gsynaptics: 
Code:
sudo apt-get install gsnyaptics.Once installed, you'll get Touchpad entry under System->Preferences. To open it, you'll need to add this line: 
Code:
 Option "SHMConfig" "true"to the touchpad section of your /etc/X11/xorg.conf file.
 sudo aptitude install gsynapticsits a GUI and will allow you to configure your touchpad

---

### Post by ataranea on 2007-02-13
in kubuntu...which one is the preferences option?

---

### Post by annda on 2007-02-13
there is a package called ksynaptics, maybe you shoud try that.

---

### Post by Bachstelze on 2007-02-13
All you need is [here](https://help.ubuntu.com/community/SynapticsTouchpad). Just do the modifications in your xorg.conf and install ksynaptics :)

---

