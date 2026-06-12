---
title: "Changing owner on mounted disk"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2006-11-27
I mounted a FAT disk to /bronty and am trying to change the ownership from root to my normal user, ephilei. I ran 

sudo chowner ephilei /bronty/ 

enter the root passwd and get the ambiguous "operation not permitted." I've made sure no other processes are using any files in it and I've tried via Nautilus. What else can I try?

---

### Post by bodhi.zazen on 2006-11-27
> **Ephilei said:**
> I mounted a FAT disk to /bronty and am trying to change the ownership from root to my normal user, ephilei. I ran 

sudo chowner ephilei /bronty/ 

enter the root passwd and get the ambiguous "operation not permitted." I've made sure no other processes are using any files in it and I've tried via Nautilus. What else can I try?

```
sudo umount /bronty
sudo mount /device/ /bronty -o uid=1000,umask=000
```

The umask is for rw permissions.....

You can also add an entry in fstab.

sudo gedit /etc/fstab

Add this:
> /device /bronty vfat users,uid=1000,umask=000 0 0

You can now mount with:```
mount /bronty
```No sudo....

---

