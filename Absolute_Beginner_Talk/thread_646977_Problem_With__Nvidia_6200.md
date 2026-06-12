---
title: "Problem With  Nvidia 6200"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-12-21
Hi... I installed the driver for my nvidia 6200 and After that i was able to startx... but after that i rebooted my Pc and it couldnt boot ubuntu... plz help 

[B]Edit: I am using ubuntu 7.10 

And this is what i read when I am trying to read:

      *Checking battery state                                          [Ok]

      *Running local boot scripts (/etc/rc.local)               [Ok] 

And then nothing....[/B]

---

### Post by spiderbatdad on 2007-12-21
try ctrl-alt-f1 to get a terminal. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Sef on 2007-12-21
What *buntu and version are you using?

> I installed the driver for my nvidia 6200

How did you install the driver?

---

### Post by Pabx on 2007-12-21
Edited my post...

---

### Post by Pabx on 2007-12-21
Any idea?

---

### Post by RomeReactor on 2007-12-21
Hi. Did you install the drivers from the repositories, or from nVidia's website? if you have an onboard video card, try disabling it in BIOS.

---

### Post by Pabx on 2007-12-21
I installed it manually ....

---

### Post by RomeReactor on 2007-12-21
Did you install any recent updates that included the kernel? if so, I think you need to reinstall them. Also make sure you have the restricted modules:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

---

### Post by PmDematagoda on 2007-12-21
How did you install the Nvidia driver manually? What steps did you follow?

And your card should be able to work like a charm on Ubuntu since my 6200 works just perfectly when I installed it's drivers using the Restricted Drivers Manager.

---

### Post by Pabx on 2007-12-21
i downloaded the driver from nvidia webpage... and i follow the instructions thats what i did ... I think it compiled a kernel or something like that... maby there is the prob

---

### Post by RomeReactor on 2007-12-21
If you haven't installed the drivers yet, I suggest you follow PmDematagoda's advice and install them from Ubuntu: go to "System->Administration->Restricted Drivers Manager" and check the box for your card.

---

