---
title: "How to install WIFI drivers with NDISWRAPPER?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by chuckcamp on 2007-02-02
I've got the drivers for my wireless network card.

I've downloaded NDISWRAPPER.

How do I install these drivers with NDISWRAPPER in the terminal?  I need step-by-step directions please.

---

### Post by mikewhatever on 2007-02-02
Try the guide [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)

---

### Post by chuckcamp on 2007-02-02
> **mikewhatever said:**
> Try the guide [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)


got this message:
**Unable to create directory /etc/ndiswrapper/bcmwl5a.Make sure you are running as root**

what the hell is this supposed to mean?

---

### Post by RomeReactor on 2007-02-02
It means that you must prepend "sudo" to any command that will make changes to the system (basically, anything that is not in your "/home/user" folder); example:

```
sudo mkdir /usr/share/games/dangerdeep
```

to make a folder called "dangerdeep" in "/usr/share/games"

---

### Post by Spr0k3t on 2007-02-02
I'm just curious.  What wifi card do you have?  I have a wireless card that is supposed to work with the latest make of NDISWrapper but it refuses to work.

For the full information, check the PCI config:
$ lspci

If you have an Atheros AR5008 chipset, start checking around for a different wireless option.

---

