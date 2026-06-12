---
title: "Kubuntu Startup Splash w/Ubuntu Install"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by fridayxiii on 2006-06-24
I have Ubuntu installed, but tried the Kubuntu/KDE desktop just for fun (installed the KDE desktop package).  After trying both out I've decided to go w/GNOME, and used the terminal commands to remove KDE.  However, now I have the blue Kubuntu-themed startup screen that appears right after the GRUB menu.  Ubuntu still boots up fine, I just have a mis-themed install.  It's no biggie, but a bit annoying for the perfectionist in me.  ;)   

Anyone tell me how to purify my cup of Ubuntu?  

Oh yeah, does the Search feature in the forums support Boolean terms e.g. AND, OR, etc.?

---

### Post by gingermark on 2006-06-24
It sounds like you're still running KDM.

Try ```
sudo dpkg-reconfigure gdm
``` and then select gdm.
EDIT: Obviously misread your post, sorry.

---

### Post by raptros-v76 on 2006-06-24
i knew how to do this. wait. here
```
 sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)

```

---

### Post by vinodis on 2006-06-25
i have the same problem.
how to resolve?
[edit]
resolved.
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

