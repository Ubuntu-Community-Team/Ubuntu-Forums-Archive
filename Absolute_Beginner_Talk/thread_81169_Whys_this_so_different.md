---
title: "Whys this so different?"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by ctcecil on 2005-10-23
Why didn't ubuntu ever prompt me for a root password during installation? Is it the same password as my user account or what? my 'fakeroot' works but access is allways denied when trying to su root...

---

### Post by xequence on 2005-10-23
You have to enable it, use:

sudo passwd root

and it will ask you what password you want to give root.

---

### Post by aysiu on 2005-10-23
This has everything you ever wanted to know about root/sudo in Ubuntu:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ctcecil on 2005-10-23
[QUOTE=aysiu]This has everything you ever wanted to know about root/sudo in Ubuntu:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

that isn't working right now, but **sudo passwd root** helped me out. thanks alot.

---

### Post by UbuWu on 2005-10-23
[QUOTE=aysiu]
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

It is now at [https://wiki.ubuntu.com/RootPrivileges](https://wiki.ubuntu.com/RootPrivileges)

---

