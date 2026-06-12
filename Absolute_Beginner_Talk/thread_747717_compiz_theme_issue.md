---
title: "compiz theme issue"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-04-06
I have installed th emerald theme manager and was wondering how do i enable ubuntu to use emerald theme instead of metacity?  i have tried compiz --replace and get this in my terimal:

ryanzec@ryanzec-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 08:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by mgmiller on 2008-04-06
Run the commands from alt/F2

To enable metacity/compiz:
  ```
gtk-window-decorator --replace

```
To enable emerald:
  ```
emerald --replace
```

To enable metacity with compiz turned off:
  ```
metacity --replace
```

---

