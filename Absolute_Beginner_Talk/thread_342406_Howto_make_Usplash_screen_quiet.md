---
title: "Howto make Usplash screen quiet??"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by !nvincible on 2007-01-20
Hi all ,

I had changed my Usplash screen ,it is working fine .But by default it is in verbose mode :( 
I want  it to be quiet ...
can anyone suggest me some thing 

Thankx in Advance

---

### Post by taurus on 2007-01-20
Put the word **quiet** in the kernel entry in /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

