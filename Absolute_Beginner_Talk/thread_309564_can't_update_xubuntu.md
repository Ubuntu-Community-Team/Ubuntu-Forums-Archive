---
title: "can't update xubuntu"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by albesan on 2006-11-29
hello team,

I get nothing but errors trying to update xubuntu not from the console not from any of the utilities probided with the distro, I haven't been able to do a single update.
is it really that hard?
I have read about alternative updaters but haven't found one yet that supports ppc arquitechture.

any help would appreciated

a.

---

### Post by pay on 2006-11-29
How are you updating? Do you mean updating 6.06 to 6.10? To update all packages execute ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by albesan on 2006-11-30
hello,
Sorry I wasn't very clear.
I just can not connect to repositories, none of them.
I don't really want to upgrade, I actually just downgraded, too many issues with the latest distro.

I went to source-o-matic, generated a list of repositories and edited my list. I tried running apt from a terminal and I got password errors. I tried to do the gpg thing with the key information on source-o-matic but it didn't work either. It said it is not a valid key ????????

All I wanted to do is check if there are any security or important system updates that I need to use to make my system more stable/reliable.

thanks for your reply

---

