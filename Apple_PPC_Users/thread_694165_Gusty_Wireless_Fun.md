---
title: "Gusty Wireless Fun"
date: 2008-02-11
forum: Apple PPC Users
---

### Post by calcioguy9 on 2008-02-11
Hey all,

So I installed Gusty on my iBook G4.  I enabled the firmware, restarted, and YES!  Network manager showed all the wireless networks and let me connect!  I then installed the updates and rebooted, but then NM said something like "No networks devices have been found."  I then guessed that one of the updates killed NM, so I reinstalled Gusty and updated everything but NM; however, again upon restart the NM gave me the same message.  So for a third time, I reinstalled Gusty, enabled the wireless, rebooted and again it worked.  This time, though, I decided I wouldn't update until I figured out which update was breaking NM, so I updated nothing.  However, when I booted up my computer this morning, NM was yet again broken!

So my question is:

Does anyone know what is breaking network manager on restarting?

---

### Post by stream303 on 2008-02-12
I found NM a bit tricky, but had to be sure I had enabled the devices.  maybe this might help:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

This was a great doc for me as it allowed me to bypass NM without totally removing it, but that's because I'm running a simple ethernet network.

---

### Post by thierryg on 2008-02-12
Hi, exactly the same behavior here on an iBook G4. Live ubuntu CD, Network Manager works fine. Install: Network Manager works fine. Install all updates: Network Manager loose all networks (no reboot, network manager loose the available devices and disconnect from the current network sometime during the update).

Manually setting the network connections (wifi/ethernet) works. IBook G4 with aiport extreme (bcm43xx) card.

> **calcioguy9 said:**
> Hey all,

So I installed Gusty on my iBook G4.  I enabled the firmware, restarted, and YES!  Network manager showed all the wireless networks and let me connect!  I then installed the updates and rebooted, but then NM said something like "No networks devices have been found."  I then guessed that one of the updates killed NM, so I reinstalled Gusty and updated everything but NM; however, again upon restart the NM gave me the same message.  So for a third time, I reinstalled Gusty, enabled the wireless, rebooted and again it worked.  This time, though, I decided I wouldn't update until I figured out which update was breaking NM, so I updated nothing.  However, when I booted up my computer this morning, NM was yet again broken!

So my question is:

Does anyone know what is breaking network manager on restarting?

---

