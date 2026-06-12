---
title: "Help with Usplash"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by cinmachina on 2007-05-19
I followed the guide here at:
[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

and now my usplash screen is non existant, it just says it has no image to view, and when I shut down and boot up it's just a bunch of processes and text. I don't know what I did, but can someone help me get back to the original screen that was installed? I don't want to mess with this anymore

Thanks!

By the way, I use Ubuntu 7.04.

---

### Post by Seisen on 2007-05-19
Just go in the terminal put these commands in and it should fix it. 

```
sudo ln -sf /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so 
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

