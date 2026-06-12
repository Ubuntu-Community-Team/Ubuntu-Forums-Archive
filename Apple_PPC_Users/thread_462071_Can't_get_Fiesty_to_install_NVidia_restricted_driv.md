---
title: "Can't get Fiesty to install NVidia restricted driver"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by iMacThere4iAm on 2007-06-02
One of the problems I'm having with Ubuntu is that it doesn't seem to want to install the NVidia restricted driver. I open the Restricted Drivers Manager and it tells me that 'No restricted drivers are needed for your system' or something along those lines. My Graphics card is on the list of supported cards (GeForce 6600) but the manager doesn't seem to recognise it.

---

### Post by steevols on 2007-06-02
First off, I'm assuming you don't already have 3D acceleration?

You should be able to manually install the driver by searching for "nvidia" in synaptic and installing the latest package from there. Once that's done, make a backup copy of xorg.conf (ctrl-alt-f2, log in, "cp /etc/X11/xorg.conf /home/*user*") and then run "nvidia-xconfig enable" or something like that. Then, restart X and you should have a working NVidia driver setup. If not, then join the masses of disgruntled 3D wannabes.

---

### Post by je m'ennuie on 2007-06-02
There is NO nvidia restricted drivers for Apple PPC, only the free nv (no 3D accelerated)
Some people are working on an open source driver with 3D enabled for nvidia cards, see [http://nouveau.freedesktop.org/wiki/FrontPage](http://nouveau.freedesktop.org/wiki/FrontPage) . But it's not ready yet.

---

### Post by linux_author on 2007-06-02
- have you tried Envy?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Auria on 2007-06-02
> **linux_author said:**
> - have you tried Envy?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

That will NOT work - the OP is using PPC Ubuntu, binary NVidia drivers are only for x86 processors, they do not work on PPC.

---

### Post by linux_author on 2007-06-02
> **Auria said:**
> That will NOT work - the OP is using PPC Ubuntu, binary NVidia drivers are only for x86 processors, they do not work on PPC.

- ackpht! you are absolutely correct!

:-(

---

### Post by stmiller on 2007-06-02
Check out the FAQs:

---

