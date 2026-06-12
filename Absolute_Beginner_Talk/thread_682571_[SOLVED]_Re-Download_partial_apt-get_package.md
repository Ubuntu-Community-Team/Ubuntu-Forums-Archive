---
title: "[SOLVED] Re-Download partial apt-get package"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-30
This should be really easy, but while using apt-get to install a package, I closed the terminal before it was done. Now it says it is installed, but I don't think all of it was done. I tried removing it, and reinstalling it, but there is no downloading (cached?). How do I get this entire package? A do-over?

---

### Post by p_quarles on 2008-01-30
You could first try:
```
sudo apt-get -f install
```
to fix broken packages.

If that doesn't take care of it, tell us what the package is.

---

### Post by imaginal on 2008-01-30
That didn't seem to help.

Mid-run of ```
sudo apt-get install ubuntu-restricted-extras
``` I closed the terminal. Some things installed fine, but I don't think everything went through. (Namely, flash videos in firefox)

---

### Post by jan quark on 2008-01-30
perhaps only flash in not working?

than try this guide to install flash via the official adobe site
[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by hyper_ch on 2008-01-30
flash auto-install is currently broken. you'll need to install it manually. Search the forums for a guide - there are plenty of those.

---

