---
title: "restricted drivers problem"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by janne5011 on 2007-10-25
Hi, when i click in "nividia..." and after choosing enable I got this msg:
"The software source for the package

   nvidia-glx-legacy

 is not enabled."

Which what I tried todo=).
thanks in advance if anyone know what to do.

---

### Post by overdrank on 2007-10-25
> **janne5011 said:**
> Hi, when i click in "nividia..." and after choosing enable I got this msg:
"The software source for the package

   nvidia-glx-legacy

 is not enabled."

Which what I tried todo=).
thanks in advance if anyone know what to do.

Hi you may check that all repos are enabled. You can check either via software source's or synaptic manager.

---

### Post by Pumalite on 2007-10-25
sudo apt-get install nvidia-glx-legacy

---

### Post by oldos2er on 2007-10-25
Go to System, Administration, Software Sources, and make sure the multiverse section is checked.

---

### Post by janne5011 on 2007-10-25
"the pkg  nvidia-glx-legacy is not available but a another pkg points to it"

that what it says in terminal after I tried the apt-get

---

