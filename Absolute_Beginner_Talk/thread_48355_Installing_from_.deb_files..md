---
title: "Installing from .deb files."
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by Umbra on 2005-07-12
If i already have or downloaded a .deb package, how do i install it? similar to tar.gz files?

---

### Post by stepper on 2005-07-12
sudo dpkg -i package.deb!

---

### Post by ubuntp on 2005-07-12
dpkg -i yourdebfile.deb

---

### Post by Norrad on 2005-07-12
Where do I place the file for dpkg to find it?

---

### Post by codejunkie on 2005-07-12
[QUOTE=Norrad]Where do I place the file for dpkg to find it?[/QUOTE]
in any directory that your have read-write access to, but it would be the best idea to place it in your home directoy though. then change to that dir with in the terminal with ```
cd /home/yourusername
``` then you can install it with
```
sudo dpkg -i packagename.deb
```

---

### Post by musicman2059 on 2005-07-12
I usually keep all my deb packages in a "debs" directory off of home.  So if you you were using my setup, you would move your files and then go like so:

```

[sudo] mv /path/to/packagename.deb /home/yourusername/debs/packagename.deb
cd /home/yourusername/debs
sudo dpkg -i  (or --install) packagename.deb
```

Try to keep yourself to only using debs from the ubuntu repository, though.  ;)

---

### Post by Norrad on 2005-07-13
Thanks everyone, managed to install NeroLinux with your help. It didn't come from the Ubuntu Repository though

---

### Post by charlieg on 2005-07-15
[QUOTE=musicman2059]Try to keep yourself to only using debs from the ubuntu repository, though.  ;)[/QUOTE]Sadly that's not always possible if the packages isn't available from the ubuntu repositories.  For instance I had to install [Stellarium](http://stellarium.sourceforge.net) as a standalone from an.deb[url=http://3demi.net/debian/debs]external resource[url] as it's just not directly avaiable for ubuntu.

---

