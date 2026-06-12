---
title: "[SOLVED] Cannot Start XServer"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Abu_Dayya on 2007-12-03
Hi all
I'm realy new to linux, so pleae bare with me
I installed Ubuntu of my desktop and it was working fine. Then, i bought a new desktop, but used the old hard disk (which had Ubuntu 7.10 already). 

Then when I try to turn my PC on, it reports an error sayng (cannot start your xserver). I tried running the live CD, but couldin't (same problem). can anyone please help? Again, I'm a total noob, so please can you explain without using too much "linux words"? lol

the new desktop specs are:
MotherBoard: Gigabyte S-series p31
CPU: Intel Core 2 Duo
Graphics Card: Nvidia NX8500GT (MSI)
RAM: 1 GB SempleTech
HD: 320 GB SATA

Thanks

---

### Post by PmDematagoda on 2007-12-03
Try this:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Sarteck on 2007-12-03
In addition to what PmDem posted (which should initially get you up and running), you might later have to muck around with nVidia drivers to get your optimal resolution.  (For that, you might want to try the Envy package.)

---

### Post by sentientd on 2007-12-03
I think I have the exact same problem... but I have no idea where to go to put in the code. It's so embarrassing! :confused:

---

### Post by Abu_Dayya on 2007-12-03
> **PmDematagoda said:**
> Try this:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thank you for your quick reply.

But how can I type this command if i can't load Ubuntu?

---

### Post by PmDematagoda on 2007-12-03
Boot Ubuntu in Recovery mode or press Ctrl+Alt+F1 when Ubuntu stops loading in Normal mode.

---

### Post by Abu_Dayya on 2007-12-03
Thanks. I'll try to do that

---

### Post by Abu_Dayya on 2007-12-03
> **PmDematagoda said:**
> Try this:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

By the way, what does this command do exactly?

---

### Post by PmDematagoda on 2007-12-03
It configures the X-server to it's default settings.

---

### Post by sentientd on 2007-12-03
> **Abu_Dayya said:**
> Thanks. I'll try to do that

For the most part this worked for me.

I have an Nvidia card as well, but I was told to select the drivers called "nv" as opposed to the ones called "nvidia" 

The first time I absentmindedly chose "nvidia" and it did not work.

Good luck! :)

---

### Post by Abu_Dayya on 2007-12-03
Ok, so i ran this command "sudo dpkg-reconfigure -phigh xserver-xorg"  and i was able to  log on to the graphical interface of Ubuntu successfully.

Then i inatalled Envy, and when i tried to install the Nvidia driver with it reports an error. And this is what it says in the log file "/var/log/envy-installer.log"

-------------
ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev
------------------------

Any help?
Thanks

---

### Post by Abu_Dayya on 2007-12-03
Can I install the driver from the Restricted drivers manager instead?

---

### Post by FuturePilot on 2007-12-03
> **Abu_Dayya said:**
> Can I install the driver from the Restricted drivers manager instead?

Yes. Give that a try

---

### Post by Abu_Dayya on 2007-12-18
Finally. Envy worked and installed the driver just fine.

I don't know what was the problem the first time

---

