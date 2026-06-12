---
title: "e17 Theme Broken"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by bobo on 2007-06-19
I was playing around the default themes that comes with e17 and I chose the "Milky" theme to see what it looks like and Applied it, and now it won't let me select any other theme.  It is almost like the selection area in non clickable now.  If I click on import, the import window will come up but cannot select on any of the files.  

Is there a way to manually reset the theme that it's using?  Say via command line?

---

### Post by Rui Pais on 2007-06-19
yes
```
mv .e/e/themes/milky.edj .e/e/themes/milky_BAK.edj
```

and restart e.

Recently themes dialog only worked with basic mode, check if it's not the case.

Check for recent versions of milky on e17 site. It's suppose to be one of the updated themes available.

Yet another way:
enlightenment_remote -theme-set theme default && enlightenment_remote -restart
:)

---

### Post by bobo on 2007-06-19
Thanks Rui, that worked.  Only my milky.edj was located under /usr/share/enlightenment/data/themes.

---

### Post by Rui Pais on 2007-06-19
Ahh  you installed using debs, i bet.

check my post again for an alternative (and more correct way)

---

