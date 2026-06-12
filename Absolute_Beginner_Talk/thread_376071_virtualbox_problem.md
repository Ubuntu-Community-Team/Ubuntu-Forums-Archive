---
title: "virtualbox problem"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by amaan on 2007-03-04
i'm running windows xp through virtualbox but when i download something on windows xp i cannot access it on ubuntu? any way i can do this...?

---

### Post by nhandler on 2007-03-04
I believe under settings in vmware somewhere, there is an option to make it so you can access your ubuntu drive from inside the virtual system. Then, you can copy files between the two.

---

### Post by amaan on 2007-03-04
im using innotek virtualbox, not vmware...is vmware open source?

---

### Post by Karl S. on 2007-03-05
Yes there's a way to access files from your guest machine in your host machine, so long as you save it to a directory that can be access by both guest and host. There's a couple ways to  set that up. Either through Samba or through the instructions in the [User's Manual]("http://www.virtualbox.org/wiki/Downloads") section 5.4, Folder Sharing.

---

