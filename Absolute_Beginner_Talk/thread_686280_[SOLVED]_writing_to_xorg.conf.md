---
title: "[SOLVED] writing to xorg.conf"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by cane1832 on 2008-02-03
OK, 

Im trying to write to the xorg.conf file cause i have compiz and the cube won't work anymore for some odd reason (was working...?)  I have been reading the site and found a post ( [http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html](http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html) ) and want to add the lines it suggests. Though ever time i open the xorg.conf file and try to save it says i don't have permission.
Just wondering how i would do this. 

Thanks from a newb

---

### Post by jaytek13 on 2008-02-03
Use sudo

```
sudo gedit /etc/X11/xorg.conf
```


gedit is gnome. If your using kde it would be kate instead.

---

