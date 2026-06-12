---
title: "[SOLVED] how can i delete wicd and go back to network manager"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by divindavid on 2008-02-28
ok i got wicd because people sayed it was good and i dont like it and i want to go back to network manager but to do that i would have to uninstall wicd how can i do that

---

### Post by divindavid on 2008-02-28
i really need to go back to network manager ecause wicd is slow for my card

---

### Post by divindavid on 2008-02-28
please

---

### Post by divindavid on 2008-02-28
it is so slow my BT DLs are at like 25 kbps

---

### Post by divindavid on 2008-02-28
please

---

### Post by Roryking on 2008-02-28
Try this at the terminal:
```
sudo apt-get install network-manager network-manager-gnome
sudo apt-get remove wicd

```

---

### Post by imdano on 2008-02-28
Wicd is unlikely to be effecting your download speeds, all it does is make calls to ifconfig/iwconfig to make a connection for you.  You could always just make a wired connection with the command line, then uninstall wicd and install networkmanager with synaptic or apt-get.

Actually, I don't think killing and uninstalling wicd will take down an active connection.  Try killing the wicd tray/daemon and see if you still have internet.  If you do, you could just install network-manager then and have no problems.

EDIT: I think that if you run ```
sudo apt-get install -d network-manager network-manager-gnome
```apt-get will just download the nm packages, without uninstalling wicd.  So once they're downloaded, you can safely uninstall.

---

### Post by divindavid on 2008-02-29
cool i did that and wicd is gone but network manager is not in the panel

---

### Post by divindavid on 2008-02-29
nvm network manager is back thanks is will mark this thred as solved

---

