---
title: "Update manger can't read lists"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-29
Something is wrong with my system its very slow, takes about 15 minutes to boot after I log in, and the graphics are off. This is the error i get when i try to update from the command line:

wolf@wolf-alteredbeast:~$ sudo apt-get install linux-restricted-modules-2.6.22-14-generic
[sudo] password for wolf:
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
wolf@wolf-alteredbeast:~$

---

### Post by harlan on 2007-11-29
Run first 
  $sudo apt-get update

and try again

---

### Post by Evil Wayz on 2007-11-29
> **harlan said:**
> Run first 
  $sudo apt-get update

and try again

it gets stuck @ 95%

---

