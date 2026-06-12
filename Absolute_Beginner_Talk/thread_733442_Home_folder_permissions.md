---
title: "Home folder permissions"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-03-23
I am playing around with home directories i just changed my home directory to a external HDD and when i try to log in i get this error

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language engine being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users."

How do i set the external HDD (media/disk) to have these permissions?

Saj

---

### Post by scragar on 2008-03-23
run:```
chmod 750 ~/ && chmod 644 ~/.dmrc
```from your nearest terminal then log out and in again.

replace 750 with 755 if you want any user to be able to view your home directory, personaly I wouldn't.

---

### Post by saj0577 on 2008-03-23
kk So change the home folder to a one that works, log in change the permissions of the home folder i want(usb), change my home folder destination to the diesired place(usb), log out and back in.

Yeah?

Saj

---

### Post by scragar on 2008-03-23
Just run that after you get the error, it correct's the perm's for the current home directory.

If you change the mount point or whatever then you also change the home directory, and the permitions change is useless.

---

### Post by saj0577 on 2008-03-23
But when it gives me the error it logs me out before i can do anything i jsut get 2 messages?
Saj

---

### Post by scragar on 2008-03-23
ok, my younger brother used to encounter this error and it would still log him in, so forgive me for missing your point.

replace ~ with whatever directory it is, so you said /media/disk
```
chmod 750 /media/disk/ && chmod 644 /media/disk/.dmrc
```

---

### Post by saj0577 on 2008-03-23
It says .dmrc does not exsists?

Saj

---

### Post by saj0577 on 2008-03-23
Do i just create one with the same contents as the ones for other users?

Saj

---

### Post by scragar on 2008-03-24
```
cp ~/.dmrc /media/disk/.dmrc
```

---

