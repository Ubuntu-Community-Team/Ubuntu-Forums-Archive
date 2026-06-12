---
title: "apt segmentation fault !!"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by NiTsi on 2005-12-02
I can't open from menu >System > Synaptic . Moerover when i do in console apt-get install filename i get :  # apt-get install openoffice.org-l10n-el
Reading package lists... Done
Segmentation faulty tree... 50%

---

### Post by kalin on 2005-12-02
It's probably corrupted apt cache, open a terminal and remove the .bin files in /var/cache/apt:

```

sudo rm /var/cache/apt/*.bin

```

Then do an update and upgrade.

---

### Post by NiTsi on 2005-12-03
[QUOTE=kalin]It's probably corrupted apt cache, open a terminal and remove the .bin files in /var/cache/apt:

```

sudo rm /var/cache/apt/*.bin

```

Then do an update and upgrade.[/QUOTE]



ok i did it and it's fine thank you veru much

---

