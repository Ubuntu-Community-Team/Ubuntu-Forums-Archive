---
title: "symlinking directory"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-11-04
just installed celestia(autopackage release from offical page).

it installed to /usr/share/celestia/ .

the extras folder where the addons are stored are in /usr/share/celestia/extras.

since my root partition isn't big enough i want to create a symlink to my /home/zekopeko/Celestia/extras folder so i can just place the addons there.

is this possible?

---

### Post by Arevos on 2006-11-04
Yes.
```
$ mkdir /home/zekopeko/Celetia
$ sudo mv /usr/share/celestia/extras /home/zekopeko/Celetia/extras
$ sudo ln -s /home/zekopeko/Celetia/extras /usr/share/celestia/extras
```You may also wish to alter the permissions on the extras folder so you can copy files in without having to use 'sudo'.

---

### Post by zekopeko on 2006-11-04
THNX! worked like a charm!

---

