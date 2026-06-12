---
title: "Ubuntu updates causes all font to appear as squares"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by jamietssg on 2007-08-14
HI

I recently installed Ubuntu and ran an update. Now all the characters appear as squares!

Any advice?

Thanks
jamie

---

### Post by DeHorde on 2007-08-14
```
sudo -s
apt-get update
apt-get upgrade
```

What is your locale by the way? ```
$ locale
``` Could it be you are trying to work with a language setting that does not have any fonts for it installed? I believe you can change the languagesetting from the GDM login window. 

If that does not do the trick this might help:
```
dpkg-reconfigure fontconfig 
```

---

