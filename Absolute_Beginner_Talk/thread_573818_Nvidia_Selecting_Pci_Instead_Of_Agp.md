---
title: "Nvidia Selecting Pci Instead Of Agp"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by mobraver on 2007-10-12
Please help I have no graphic in Ubuntu.  
I have error: No device detected,  no screen found.
Because  it indicates: (Bus ID PCI:1:0:0) found But my card is in an agp slot not pci.

---

### Post by dcstar on 2007-10-12
> **mobraver said:**
> Please help I have no graphic in Ubuntu.  
I have error: No device detected,  no screen found.
Because  it indicates: (Bus ID PCI:1:0:0) found But my card is in an agp slot not pci.

Install the **discover1** and **xresprobe** packages, then - in a terminal - do:
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

