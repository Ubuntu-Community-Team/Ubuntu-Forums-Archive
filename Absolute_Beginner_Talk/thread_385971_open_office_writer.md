---
title: "open office writer"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by SMS on 2007-03-16
hey when i load open office (eg writer or speedsheet etc) the loading window comes on the disappears and oo doesnt load, mmmmm.
so i ran it in terminal and i get this
> 
sms@sms-laptop:~$ oowriter
/usr/lib/openoffice/program/javaldx: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
head: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
find: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
/usr/lib/openoffice/program/pagein: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header
/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: /usr/lib/libc.so.6: invalid ELF header

** (process:7543): WARNING **: Unknown error forking main binary / abnormal early exit ...
sms@sms-laptop:~$ 

whats going on thanks guys u rule

---

### Post by SMS on 2007-03-16
(btw please exuse my typos)

---

### Post by SMS on 2007-03-16
come on guys i seriously need your help

---

### Post by Najand on 2007-03-16
Try to reinstall "libc6" using:
```

sudo aptitude reinstall libc6

```

---

### Post by SMS on 2007-03-17
hey thanks fo the reply but it says "re-install" is not a valid otion

---

### Post by Najand on 2007-03-17
Sorry  it is "aptitude" not "apt-get"... My careless mistake...

---

### Post by SMS on 2007-03-17
sms@sms-laptop:~$ sudo apt-get reinstall libc6
E: Invalid operation reinstall
sms@sms-laptop:~$ sudo apt-get re-install libc6
E: Invalid operation re-install
sms@sms-laptop:~$

---

### Post by AtrejuT on 2007-03-17
sudo aptitude reinstall libc6
doesn't work? it should...
You could just try doing it in synaptic (look for libc6, right click, chose reinstall, click apply)

---

### Post by SMS on 2007-03-17
nope still hasnt worked
this is soo frustrating it was working brilliantly before

---

### Post by SMS on 2007-03-18
i fixed it thanks read my other post to see how (search sms in the seach bar)

---

