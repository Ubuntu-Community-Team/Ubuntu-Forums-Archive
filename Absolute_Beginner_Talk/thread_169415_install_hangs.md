---
title: "install hangs"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by tor@hegna.net on 2006-05-02
I have ha PII with 64 mb ram and 100g hd. When I install ubuntu the system hangs when I come to the partision area. What can I do. Ditch the computer ??:)

---

### Post by cgjones on 2006-05-02
I ran into a similar problem with an older computer. Is it hanging at 33%? Check your BIOS to see if it supports ACPI. If not, you could try the following when you boot the install disk. Also, you should check to see if the computer supports large drives.
```

linux pci=noacpi

```

---

### Post by tor@hegna.net on 2006-05-02
I cant find the = sign on the keyboard because I have a norwegian keyboard and  this is before the program has installet the norwegian keyboard driver. How can I get the =

---

### Post by tor@hegna.net on 2006-05-02
It is firs going to 100% on the partision area then the screen turns blue and 3-4 sec. after that it is completely hangman.

---

### Post by cgjones on 2006-05-02
Ok, that doesn't sound like the same problem I had.

---

