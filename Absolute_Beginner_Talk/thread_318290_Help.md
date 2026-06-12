---
title: "Help"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by maggiymir on 2006-12-13
Hi
I have now reinstalled my ubuntu.
My home folder in on a different partition and now I have created the users again but I am not allowed to access the folders.
What do I do ?](*,)

---

### Post by bodhi.zazen on 2006-12-13
> **maggiymir said:**
> Hi
I have now reinstalled my ubuntu.
My home folder in on a different partition and now I have created the users again but I am not allowed to access the folders.
What do I do ?](*,)

```
sudo mkdir /mnt/old_home
sudo mount /dev/hdxy /mnt/old_home
sudo chown root:users /mnt/old_home
sudo chmod 770 /mnt/old_home
```

If that fails, you can always:
```
sudo chmod -R 777 /mnt/old_home/*
```

---

