---
title: "grub on /dev/sda3"
date: 2010-10-25
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2010-10-25
I installed Lucid Lynx on my MacBook 2,1. I was so stupid to have Grub installed on /dev/sda3, which does not seem to work. The old-fashioned /dev/sda (by forcing it), works well. But now I have two Linux entries in rEFIt. Does anyone have a solution how to get rid of Grub on /dev/sda3 ?

I tried
```
dd if=/dev/zero of=/dev/sha3 bs=440 count=1
```
but that did not work.

---

