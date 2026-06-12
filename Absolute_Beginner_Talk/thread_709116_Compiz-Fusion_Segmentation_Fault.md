---
title: "Compiz-Fusion Segmentation Fault"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by hammad1337 on 2008-02-27
I was running compiz fine until I rebooted.
I am using a single monitor and have made no changes whatsoever, to my pc since the last time compiz-fusion was working.
Now when I try to:
```

$ compiz --replace &

```
i get:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5159 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Segmentation fault (core dumped)

```

Any ideas what may have gone wrong? :confused:

---

### Post by Monster_user on 2008-03-05
I'm having the same problem with Kubuntu 7.10. "kde-window-decorator" works, with all of the 3D effects, except for the transparencies, and reflections.

---

### Post by bluej100 on 2008-04-15
I got this working after enabling Twinview ([http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)) and AddARGBGLXVisuals ([http://ubuntuforums.org/showthread.php?p=2121656](http://ubuntuforums.org/showthread.php?p=2121656)). Good luck!

---

