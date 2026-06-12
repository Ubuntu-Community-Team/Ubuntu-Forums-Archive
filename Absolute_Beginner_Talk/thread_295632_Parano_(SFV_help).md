---
title: "Parano (SFV help)"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by mewithoutyou on 2006-11-08
hi. so i have installed [parano]("http://parano.berlios.de/") , but when i try to open a .sfv file with it nothing happens. 

also when i type 'parano' in terminal i get '/usr/bin/env: python -tt: No such file or directory'

if anyone could help me out with this, or have another way to verify these files, that would be great.

::mWy::

---

### Post by allo2u on 2007-07-11
You can try cksfv, a commandline tool to check sfv en md5 hashes.

```
sudo apt-get install cksfv
```

If you have used a manual installation from source, try to install the .deb file from [http://developer.berlios.de/project/showfiles.php?group_id=2384]("http://developer.berlios.de/project/showfiles.php?group_id=2384")
I think you are missing some dependencies, which installing the deb might fix.

---

