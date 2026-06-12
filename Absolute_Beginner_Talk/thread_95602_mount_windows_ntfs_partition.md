---
title: "mount windows ntfs partition"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by wakatobi on 2005-11-26
how can I mount windows ntfs partition ? can I copy files on this partition ? I lost hal.dll file and I want to copy this file to windows\system32 directory:confused: 

thank's

---

### Post by Qrk on 2005-11-26
If you want the windows drive automatically mounted at bootup. Just

```
sudo mkdir /windows
```
```
sudo gedit /etc/fstab
```

and add

/dev/hda1       /windows 	ntfs    umask=0222        0       0


Which will mount your windows in /windows. You can change that folder to anything you want. This assumes you have windows on hda1 (which if you don't know where you have it, is where you have it) Then,

```
mount -a
```

You can also mount on the fly with the mount command.

---

### Post by wakatobi on 2005-11-27
thank's for your help

---

### Post by sjh on 2005-11-27
[QUOTE=wakatobi] can I copy files on this partition ? I lost hal.dll file and I want to copy this file to windows\system32 directory:confused: 

thank's[/QUOTE]

Writing to a windows NTFS partition from Ubuntu is not recommended.  Best you read here:

[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

---

