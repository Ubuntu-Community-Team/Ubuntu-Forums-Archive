---
title: "8800GTS still won't work.. need help ASAP"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by showty on 2007-06-15
I have manually installed the Nvidia drivers as per instructions here:

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

but it still won't work. I had to reconfigure the xserver to use 'nv' (it woudlnt boot after the Nvidia automatic xconfig configuration process) but that didnt work either, so I went back to 'nvidia' in the config and it booted into xserver, but without hardware rendering still..

What have I done wrong? Need help ASAP .. :(

---

### Post by showty on 2007-06-15
bump! come on please help me!!

---

### Post by showty on 2007-06-15
I have the 100.14.09 drivers installed but they won't work come on please help!

---

### Post by miceagol on 2007-07-05
Please have a look at [my post here]("http://ubuntuforums.org/showpost.php?p=2969533&postcount=169"). You have to revert to older nVidia drivers. I tried 97.55, and they work fine.

---

### Post by Raineer on 2007-07-05
97.55 worked for me well too.  However, you need to know which version of drivers your kernel is currently built for.  If you use the "Envy" script, you should be able to use the latest drivers as it will rebuild the kernel for you to use a newer version.

If the kernel's version and the installed version don't match, X won't start (but /var/log/Xorg.0.conf will tell you exactly that).  It will tell you what version the kernel is expecting, and the default from the Ubuntu CD is 97.55

---

