---
title: "Dual Booting??"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by nevertheless on 2007-03-08
Ok I have a little problem that I'm sure on of you guys can solve. I want to dual boot ubuntu and windows xp. I have both installed on my computer now so I can have a choice of what OS I want to useon startup. Now that their both installed what do I do in order to have these two dual boot.

---

### Post by dstew on 2007-03-08
You need to install a boot loader that will give you the option of picking one OS or the other at boot time. The two I know about are the old LILO (LInux LOader), and the newer Grub. You can run grub and install it using the Ubuntu Live CD.

---

### Post by Ferri on 2007-03-08
You should install Grub in your mbr. Usually you should have it installend during a normal Ubuntu install.

---

### Post by haelters on 2007-03-08
If I understand correctly you already have a dual boot. On startup you can pick one or the other. It is, however, not possible to have them boot at the same time. If you want to run at the same moment both linux and windows, you should take a look at virtualization (vmware, ...). Ubuntu can than be the host OS and Windows the guest or vise-versa. 
More information on virtualization can be found on Wikipedia: [http://en.wikipedia.org/wiki/Virtualization](http://en.wikipedia.org/wiki/Virtualization)

Hope it helps !

---

### Post by nevertheless on 2007-03-08
> **haelters said:**
> If I understand correctly you already have a dual boot. On startup you can pick one or the other. It is, however, not possible to have them boot at the same time. If you want to run at the same moment both linux and windows, you should take a look at virtualization (vmware, ...). Ubuntu can than be the host OS and Windows the guest or vise-versa. 
More information on virtualization can be found on Wikipedia: [http://en.wikipedia.org/wiki/Virtualization](http://en.wikipedia.org/wiki/Virtualization)

Hope it helps !

yes...this is what I'm trying to do. I saw it on a ubuntu video and I was real interested. I didn't mean dual boot srry. But yea I already have dual boot then

EDIT: and he had windows xp on one of the other sides of the cube while linux where on the others. This is what I want to do

---

### Post by haelters on 2007-03-08
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

Hope it helps !

---

### Post by Milt888 on 2007-03-08
This little program solved all the mysteries and problems involved with dual booting for me.

[http://www.ubuntuforums.org/showthread.php?t=228104](http://www.ubuntuforums.org/showthread.php?t=228104)

Hope it helps.

---

