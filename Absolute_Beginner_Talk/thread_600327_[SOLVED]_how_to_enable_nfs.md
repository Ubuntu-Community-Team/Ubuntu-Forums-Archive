---
title: "[SOLVED] how to enable nfs"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-02
i right clicked a folder and (i don't remeber what exactly happen) a dialogue asked me too choose if i want to share it via smb or nfs. i chose smb and it started to download something from the net. and it works with my ms win machine. but now i also want to enable nfs, but there's nowhere to get the dialogue box to pop up again. what to do?

---

### Post by argie on 2007-11-02
I sort of remember what packages were downloaded when I enabled it:
nfs-common
nfs-kernel-server

I think I remember a nfsutils also but that's not in the Package Manager, so it must be just me imagining. So
```
sudo aptitude install nfs-common nfs-kernel-server
```

---

### Post by afeasfaerw23231233 on 2007-11-02
it works. thanks

---

