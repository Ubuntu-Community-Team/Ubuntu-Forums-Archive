---
title: "my synaptic package manager is getting this problemm while opening"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by ambi1 on 2007-12-20
when i m trying to use my synaptic package manager it is showing this error.......:confused:

E: Syntax error /etc/apt/apt.conf.d/30cache:2: Extra junk at end of file

---

### Post by aktiwers on 2007-12-20
Try this:
```
sudo apt-get autoremove
```
```
sudo apt-get install -f
```
```
sudo apt-get update
```

If that doesn't work you could try delete that file. It looks like a temp file, and I don't have it on my system.. just checked. 


But before you delete it, wait till someone confirm you will be alright doing so, because I'm not sure.

---

