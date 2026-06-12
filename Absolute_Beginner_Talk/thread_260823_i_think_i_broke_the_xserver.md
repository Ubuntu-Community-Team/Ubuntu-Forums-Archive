---
title: "i think i broke the xserver"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-09-19
i added my horiz + vertical refresh rates to my xorg.conf file and saved them then restarted the xserver. now i have to gui. when i try to dpkg reconfigure my xserver it says xserver not installed...any ideas??

---

### Post by Brunellus on 2006-09-19
command is

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by swp6499 on 2006-09-19
tried that says xserver not installed??

---

### Post by Brunellus on 2006-09-19
> **swp6499 said:**
> tried that says xserver not installed??
did you try it exactly?  the xserver package is 'xserver-xorg'

---

### Post by swp6499 on 2006-09-19
yes i tried that exactly and it says xserver not installed

---

### Post by Brunellus on 2006-09-19
> **swp6499 said:**
> yes i tried that exactly and it says xserver not installed
sudo apt-get install xserver-xorg

---

### Post by swp6499 on 2006-09-19
tried that and it says package xserver-org cannot be found??? im truly lost here

---

### Post by Brunellus on 2006-09-19
do you have an internet connection or an ubuntu isntall CD?

try the whole metapackage

sudo aptitude isntall xorg

---

### Post by swp6499 on 2006-09-19
i fixed by redeiting my xorg file....but thanks for all your help...i really appreciate it

---

