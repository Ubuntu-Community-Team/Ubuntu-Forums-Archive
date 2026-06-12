---
title: "I need a Help!"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by budxbr on 2005-12-15
Hi all,
  I download the Ubuntu Brazilian Version, but i don't know to use the graphic mode.
  And install the application, but the i find a manual (only for applicattions).
  I need help to use the graphic mode!
  You can replie in Portuguese, Spanish or English.

Tanks all,
Bye

---

### Post by NotJustANewbie on 2005-12-15
Has gdm started running? Have you installed an xserver? You may need to re-configure your xserver:

If it is xorg,
```
sudo dpkg-reconfigure xserver-xorg
```

if it is xfree86,
```
sudo dpkg-reconfigure xserver-xfree86
```

You might have to install one of the above packages for the graphical environment to work.

---

### Post by hesee on 2005-12-15
have you tried to start the gui from command line:
```
startx
```

If its not working, what kind of errors do you see? (You might end up needing command NotJustANewbie provided above. If I'm not mistaken,  ubuntu uses xorg, as a default at least)

---

### Post by budxbr on 2005-12-23
Tanks

---

