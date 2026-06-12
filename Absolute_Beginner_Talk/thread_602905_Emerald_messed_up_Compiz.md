---
title: "Emerald messed up Compiz"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by alsamman on 2007-11-04
I did a fresh new installation of Gutsy and I had Compiz woriking. Everything was working fine until I wanted to install emerald, I went into synaptic and searched emerald and it said that it needed to be upgraded. I tried to but I got an error so I decided to remove emerald and reinstall it. When I tried to install it I got an error
```

emerald:
 Depends: libemeraldengine0 but it is not going to be installed
 Depends: libwnck18 (>=2.15.90) but it is not installable

```
I tried installing though terminal the other emerald packages and it still got errors. Then I realized not much longer that compiz wouldnt work anymore and the manager also wouldnt open anymore. I tried compiz --replace but that didnt do anything.
So how can I fix all of this? (Get compiz working again and working installation of emerald)

---

### Post by alsamman on 2007-11-04
Now when I try running compiz --replace in terminal rather than alt f2 I get this
```

compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by alsamman on 2007-11-04
bump

---

