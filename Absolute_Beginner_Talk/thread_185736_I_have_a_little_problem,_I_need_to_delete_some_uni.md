---
title: "I have a little problem, I need to delete some unimportant files"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Azzozhsn.NET on 2006-06-01
Hi, 
Last night I updated my system, and that required to download many packages. then I tryed to change desktop, but I can not login, I think that becuse the root partition almost full, I do not want to reinstall Ubuntu, just I need to know whare are these packages stored, I want to delete them, I can access to bash now.

thank you a lot.

---

### Post by ProjectGod on 2006-06-01
at the prompt:

**df -m**
check how much space youre using... then

**sudo apt-get autoclean**
**sudo apt-get clean**
then recheck

**df -m**
:D

---

### Post by Azzozhsn.NET on 2006-06-01
Well done, thank you very much.

---

