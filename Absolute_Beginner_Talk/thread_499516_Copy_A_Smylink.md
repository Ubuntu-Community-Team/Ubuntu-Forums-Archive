---
title: "Copy A Smylink"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by lex1 on 2007-07-12
I have been given this instruction

copy /boot/config-$(uname -r) to /usr/src/linux/.config and the symlink /usr/src/linux pointing to /usr/src/linux-source-2.6.18 

ok the fist bit i know ie
 cp /boot/config-$(uname -r) /usr/src/linux/.config
 

its the last part of the instuction I am not sure how to cp

lex1

---

### Post by annda on 2007-07-12
you can do this
```

sudo ln -s /usr/src/linux-source-`uname -r` /usr/src/linux
```

what are you trying to do?

---

### Post by lex1 on 2007-07-13
I am following a howto to set up truecrypt.

thanks for your post.

lex1

---

