---
title: "how do i share a folder"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by unseenbeing on 2007-04-12
i am making a media pc that has ubuntu 6.10 on it

i want to make my movies folder share able so i can drop my movies from my windows pc to my linux pc

how do i do this

i can access my xp pc from linux but cant acces linux from my xp

---

### Post by Bushfire on 2007-04-12
Make a FAT partition (both XP and Linux can read and write to this natively). Mount it somewhere on your Ubuntu system, and XP should see it automatically and assign it the next available drive letter.

---

### Post by justleen on 2007-04-12
i think the OP wants to share it over the network?

---

### Post by unseenbeing on 2007-04-12
yes its over a network

---

### Post by justleen on 2007-04-12
samba, or NFS would be the answer then.

try a google search on "ubuntu samba how to"   or NFS.. 
both are quite easy to set up.. (im @work, otherwise i gave you the how to myself..)

---

