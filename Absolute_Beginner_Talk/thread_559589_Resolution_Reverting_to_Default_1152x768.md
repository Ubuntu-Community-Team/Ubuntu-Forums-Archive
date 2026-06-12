---
title: "Resolution Reverting to Default 1152x768"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by cinaibur on 2007-09-25
Hey guys. I ran ENVY last night and got all my Nvidia drivers. I can change my resolution now and everything works fine, but when I restart, my resolution always changes back to 1152x768. Anybody know what's going on and how I can fix it?

---

### Post by overdrank on 2007-09-25
> **cinaibur said:**
> Hey guys. I ran ENVY last night and got all my Nvidia drivers. I can change my resolution now and everything works fine, but when I restart, my resolution always changes back to 1152x768. Anybody know what's going on and how I can fix it?

Hi you may try and use the command 
```
sudo nvidia-settings
```
This will allow you to save your settings

---

### Post by cinaibur on 2007-09-26
This did work to take me to Nvidia settings, but when I try to save is says this: Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.  What does that mean and how do I fix it?

---

### Post by alienexplorers on 2007-09-26
Try running:

> gksudo nvidia-settings

---

### Post by maduranga on 2007-09-26
"sudo dpkg-reconfigure xserver-xorg"   

 using the above command you can select the resolution that to be used by the default, But i'm not sure if this will lose any configuration you have made already to xorg. but this helps me alot.

anyway, selecting inappropriate options will cause problems.

---

### Post by cinaibur on 2007-09-26
thanks alienexplorers. it worked

---

### Post by overdrank on 2007-09-26
> **alienexplorers said:**
> Try running:

Thanks alien lesson learned:)
gk

---

