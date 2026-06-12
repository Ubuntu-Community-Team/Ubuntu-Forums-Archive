---
title: "Just wondering about apt-get"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-08-04
I see a lot of posts on almost every post telling to apt-get *file* Now I'm wondering where you get the list for all the files available with apt-get. I am mainly using Synaptic, but it would be nice to know cause synaptic often don't show the specific file as requested by the apt-get call.

---

### Post by jasmuz on 2005-08-04
Files available with apt-get? 

you do a search like this: sudo apt-cache search whateveryoulookfor :)

---

### Post by UbuWu on 2005-08-04
Apt-get uses the package name which is the same in synaptic. The actual file name is different for each version of a program. Dpkg -i for a .deb needs the exact file name.

---

