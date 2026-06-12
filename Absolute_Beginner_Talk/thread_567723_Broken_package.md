---
title: "Broken package"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-10-04
Im running Gusty Tribe 5 on my computer. I was updating and i got a "Broken package error"' so i went to the synaptic package manager.  And i ran the fix broken package command. It gave me this error. 

E: /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb: trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0

What can i do to fix this?

---

### Post by RomeReactor on 2007-10-04
Hi. Have a look at [this post]("http://ubuntuforums.org/showpost.php?p=3475508&postcount=4") (run the steps after the bug report).

---

### Post by rsambuca on 2007-10-04
There are already multiple posts on this.  A simple search would have found them.  It has been fixed in this thread:

[http://ubuntuforums.org/showthread.php?t=567185](http://ubuntuforums.org/showthread.php?t=567185)

---

### Post by Benifited on 2007-10-04
Sry. thx

---

### Post by Benifited on 2007-10-04
Is there a fix for the cupsys error?

---

### Post by Benifited on 2007-10-04
this is the new error that i get.

E: /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb: trying to overwrite `/usr/share/doc/libcupsys2/CREDITS.txt', which is also in package libcupsys2

---

### Post by RomeReactor on 2007-10-04
Same as the Gimp error: just substitute the Gimp package for the Cupsys one:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb
```
and
```
apt-get -f install
```

For bugs and errors regarding Gutsy, please go to the [Development (Gutsy Gibbon)]("http://ubuntuforums.org/forumdisplay.php?f=238") section of these forums.

---

### Post by Benifited on 2007-10-04
thx a lot bro. :)

---

### Post by macogw on 2007-10-05
Don't force overwrite.  The packages were fixed in the repos within a couple hours.  They had to tack stuff onto the fixed packages to go fix the fact that a bunch of people went and overwrote what they shouldn't have.

---

