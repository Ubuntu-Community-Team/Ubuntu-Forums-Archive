---
title: "User name and login password????"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by magic_mountain on 2006-07-21
Dear All,

I installed Ubuntu a couple months ago and has forgotten the password. Is there anyway that i can reset the password with out reinstalling the software.

Any help is appreciated.

---

### Post by cilynx on 2006-07-26
You can boot an Ubuntu Live CD.
Mount the root partition of the HD somewhere like /mnt on the Live System
```

$ sudo chroot /mnt
# passwd [username]

```
lose the [] and substitute the proper username

Physical access is the antithesis of security.

---

### Post by aysiu on 2006-07-26
If you don't have the live CD, you can also boot into recovery mode and do ```
passwd magicmountain
```

---

