---
title: "Can't activate an ATI driver"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by GearedForWar on 2007-10-27
I can't for some reason activate my ATI accelerate Graphics Driver.  I get the following error:

Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist.

Its true that xorg.conf does not exist and I know because I tried accesing it and I couldn't get to it.  any one know what this xorg.conf is and how i can get it?

---

### Post by Maestro23 on 2007-10-27
> **GearedForWar said:**
> I can't for some reason activate my ATI accelerate Graphics Driver.  I get the following error:

Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist.

Its true that xorg.conf does not exist and I know because I tried accesing it and I couldn't get to it.  any one know what this xorg.conf is and how i can get it?

Post your xorg.conf file.  Enter the followng commands in a terminal:

> cat /etc/X11/xorg.conf

***X11 (Captial X)**

---

### Post by Crafty Kisses on 2007-10-27
> **Maestro23 said:**
> Post your xorg.conf file.  Enter the followng commands in a terminal:



***X11 (Captial X)**

Yep, files and folders are case sensitive.

---

### Post by GearedForWar on 2007-10-27
> **Codename said:**
> Yep, files and folders are case sensitive.

I know, when I tried that command: cat /etc/X11/xorg.conf  , it just says that theres no such file or directory.

---

### Post by Presto123 on 2007-10-27
I had this problem too after I tried to install too many drivers. I believe I had installed the nvidia driver and then installed Envy...bad move.

But, I fixed it, finally.

---

