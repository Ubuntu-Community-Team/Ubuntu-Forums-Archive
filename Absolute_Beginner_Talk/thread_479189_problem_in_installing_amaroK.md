---
title: "problem in installing amaroK"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Siddharth Yadav on 2007-06-20
well...i tried to install amaroK by giving
sudo apt-get install amarok
and got--

Package amarok is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package amarok has no installation candidate

wats wrong? :(

---

### Post by orange2k on 2007-06-20
Try to install Amarok from the Add/remove programs list...

---

### Post by dfreer on 2007-06-20
This probably means that your repository list is broken, as amarok should be available by default.
Can you post your /etc/apt/sources.list?
Also, don't know if you tried doing this already, but it couldn't hurt:
```
sudo apt-get update
sudo apt-get install amarok
```

---

### Post by NeoLithium on 2007-06-20
I have an answer in your original post that will fix your sources.list and allow you to install what you need :)

---

