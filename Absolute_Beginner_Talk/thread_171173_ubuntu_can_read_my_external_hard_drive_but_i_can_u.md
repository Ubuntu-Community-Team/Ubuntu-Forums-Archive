---
title: "ubuntu can read my external hard drive but i can use &gt;&gt;&gt;help plzz"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by didi47 on 2006-05-06
hi guys

what's up ?od bl

my ubuntu can read my usb external hard drive but i can't cut from it or paste in it so plzzzzz help me .


god blass you :rolleyes:

---

### Post by TheTux on 2006-05-06
what is ur external hd filesystem?

---

### Post by didi47 on 2006-05-06
windows NTFS:p

---

### Post by Mustard on 2006-05-06
[QUOTE=didi47]windows NTFS:p[/QUOTE]

Reading from it should be fine, but you won't be able to write to an NTFS filesystem from linux.

---

### Post by TheTux on 2006-05-06
u can't write into ntfs partition...change it to fat.

---

### Post by didi47 on 2006-05-06
how ?

---

### Post by tommcd on 2006-05-06
If my understanding is correct, linux can read NTFS drives, but can not write to them. Linux can read and write to FAT32.
I copied some windows NTFS documents from my windows PC onto a CDR and copied them to my Ubuntu PC. When I read them I get a message that says 'do you want to run XXX? XXX is an executable file.' I just click the button that says 'read', not 'run'. I can then read them just fine.

---

### Post by manicka on 2006-05-06
[QUOTE=TheTux]u can't write into ntfs partition...change it to fat.[/QUOTE]

I'd suggest doing it from within windows to maintain data

---

### Post by Rinzwind on 2006-05-06
[QUOTE=didi47]how ?[/QUOTE]

From NTFS to FAT32 without erasing your disc is only possible with 3rd party software (Partition Magic for instance).

---

