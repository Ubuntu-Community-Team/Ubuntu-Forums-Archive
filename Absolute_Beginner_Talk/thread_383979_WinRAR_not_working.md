---
title: "WinRAR not working?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by buried on 2007-03-13
I'm using edgy eft and trying to extract a .RAR file but Archive manager is not letting me so I type sudo apt-get install rar or something like that but terminal says this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
burned@burned-laptop:~$ Please Help
BASH$: contacting Ubuntu Forums

---

### Post by nalmeth on 2007-03-13
Enable Restricted and Multiverse in your sources.list (because I can't remember which it is :) )
If you're unsure about that, click this link:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then its easy as:
```
sudo apt-get update
sudo apt-get install unrar
```

---

