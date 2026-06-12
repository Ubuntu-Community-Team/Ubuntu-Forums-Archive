---
title: "Static Home Directory Question"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by 92bek on 2007-08-28
I want to set-up my configuration to where my home directory/profile settings are on a separate partition from the OS partition.  The reason I want to configure the system this way is to allow for easier upgrades and I'll be tinkering around with the OS.  It's inevitable that I'll hose the system and lose everything on the partition.  What's the best way to integrate a /home directory to a system, save files and be able to use it for several install's?  Is there an easy to implement feature of keeping your "profile" separate?

Cheers!

---

### Post by Mornedhel on 2007-08-28
At install time, you may specify a separate partition for the /home mountpoint.

---

### Post by expatCM on 2007-08-28
and after install time, what do you edit?

---

### Post by diatribe on 2007-08-28
after you have installed there is nothing else to do

---

### Post by AnRa on 2007-08-28
> **expatCM said:**
> and after install time, what do you edit?You have to edit /etc/fstab ;)

---

