---
title: "cant see windows"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by stfury on 2007-10-24
hi guys,

soz for the nuubosity.

i have a dual boot xp and gutsy. i can boot to either in the bios.

once i have logged into ubuntu and im using it how do i access the partition on which windows is installed - i did it earlier but i cant remember how to get back.

pls help 
stfury

---

### Post by Qwerty_ on 2007-10-24
If the windows partition is using a NTFS format then you will need to install ntfs-config which will enable Ubuntu to beable to access the drives.

You can do this with the following command

```
sudo apt-get install ntfs-config
```

then once it has installed

```
sudo ntfs-config
```

Select your required options :)

---

### Post by stfury on 2007-10-24
ty alot it worked

---

### Post by Maestro23 on 2007-10-24
> **stfury said:**
> ty alot it worked

Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

### Post by Qwerty_ on 2007-10-24
Not a problem stfury.

---

