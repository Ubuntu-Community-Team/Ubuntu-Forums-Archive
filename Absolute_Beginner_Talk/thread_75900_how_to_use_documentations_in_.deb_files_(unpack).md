---
title: "how to use documentations in .deb files (unpack)"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by seigologies on 2005-10-14
i am download documentations at packages.ubuntu.com..
all files in .deb files, now i dont know how to use..

some one know how to plz teach me

---

### Post by adwait on 2005-10-14
install the deb packages using
```
sudo dpkg -i <filename>
```

Now the documentation will probably get installed to man pages. Try man, otherwise just find it using the locate command.

---

