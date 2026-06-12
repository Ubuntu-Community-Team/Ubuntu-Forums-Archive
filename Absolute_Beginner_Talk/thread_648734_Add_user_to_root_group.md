---
title: "Add user to root group?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-12-23
ok i did something stupid. i unchecked the box under permissions > ksoviero (my username), that says administer system, and now i cant do anything! i know im an idiot! anyway help!

ok, that was confusing, basically i opens the users and groups thing under System > Adminstation > Users And Groups. clicked on my name, and then clicked properties, the went into my permissions (the tab in the middle) and unchecked the box next to administer system. now i can use my programs and everything, but cant do anything system-wise! help!

---

### Post by PinkFloyd102489 on 2007-12-24
You should still be able to sudo.


Open a terminal and run 'users-admin'.

---

### Post by kevin11951 on 2007-12-24
no, i already tried that, it just tells me i have no root privileges?

---

### Post by staticvoid on 2007-12-24
do u know your root password?

su

and *then *change your users properties.

---

### Post by kevin11951 on 2007-12-24
> **staticvoid said:**
> do u know your root password?

su

and *then *change your users properties.

isn't your root password random, and the first user just has root privileges, in any case that didn't work.

---

### Post by stroyan on 2007-12-24
You could reboot and choose 'recovery mode' from the grub menu.
That should boot in single user mode as root.
Then edit /etc/group and add your account name to the line for the 'admin' group.

---

### Post by hyper_ch on 2007-12-24
> **kevin11951 said:**
> isn't your root password random
no, root is by default deactivated.

---

### Post by kevin11951 on 2007-12-24
> **stroyan said:**
> You could reboot and choose 'recovery mode' from the grub menu.
That should boot in single user mode as root.
Then edit /etc/group and add your account name to the line for the 'admin' group.

ok, that worked, i now have administering rights, thank all of you for your help though!

---

