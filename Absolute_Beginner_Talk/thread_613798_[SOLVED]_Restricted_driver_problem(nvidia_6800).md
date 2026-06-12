---
title: "[SOLVED] Restricted driver problem(nvidia 6800)"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by White-Wolf52 on 2007-11-15
hey, im new to ubuntu(not linux, my bro had me on gentoo and helped me with that) but im having a problem with the nvidia restricted driver, when i try to enable it, it comes up with the error: 
"The software source for the package

   nvidia-glx-new

 is not enabled."

if anyone has had this problem and can help, i will be gratefull :D

---

### Post by Inxsible on 2007-11-15
System>>Administration>>Software Sources. Enable the Universe and Multiverse repos. Then```
sudo aptitude update
```Then try installing the Restricted Drivers again.

---

### Post by White-Wolf52 on 2007-11-15
thx a ton, also, could u describe what that command line does?

---

### Post by Inxsible on 2007-11-15
> **White-Wolf52 said:**
> thx a ton, also, could u describe what that command line does?It updates the list of repositories. so that when you install stuff, it will now search in the newly added repos too.

Please mark you thread as solved. Thread Tools>>Mark thread as solved.

---

