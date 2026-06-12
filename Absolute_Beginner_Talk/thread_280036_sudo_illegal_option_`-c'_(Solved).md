---
title: "sudo: illegal option `-c' (Solved)"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-10-18
I am trying to install qt4 and am having a problem at the very end. The install notes say to run:

su -c "make install"

but that gives me the message:

su: Authentication failure
Sorry.

I tried:

sudo -c "make install"

but that gives me the error:

sudo: illegal option `-c'


How can I finish installing this thing?

---

### Post by taurus on 2006-10-18
Try

```

sudo make install
-or-
sudo make checkinstall

```

---

### Post by jordanmthomas on 2006-10-18
how about this?
```
sudo make install
```
It's the same as
```
su -c "make install"
```

---

### Post by Malakia on 2006-10-18
If that doesn't work you can always install it through synaptic or apt-get.

---

### Post by beamo on 2006-10-18
Thanks a lot you guys, that was a big help.

---

