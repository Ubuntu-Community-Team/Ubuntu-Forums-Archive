---
title: "Cd's arent found anymore"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by NoSmokingBandit on 2007-08-06
Earlier today i made an audio cd, but now when i put a blank cd in, it doesnt show up on my desktop. The cd i made earlier i tested, but now it isnt mounted either.

---

### Post by family on 2007-08-06
D'you scratch the CD horribly? Did you uninstall any GStreamers, Serpintine, or mess with audio settings (Sys->Pref->Sound)? If so: reinstall / revert them. If not, try Gmount-iso (from Add-remove apps). Probably not gonna do you any good though. Srry.

---

### Post by NoSmokingBandit on 2007-08-06
the cd surfaces are fine, but i did get rid of serpentine because it refused to work. I'll reinstall it and get back to you.

Edit:

Nope, serpentine didnt help at all.

---

### Post by alienexplorers on 2007-08-06
Check in your fstab file and make sure cdrom is still listed.  If not add it back in.

---

### Post by NoSmokingBandit on 2007-08-07
oddly enough a reboot solved this. But i thought linux was supposed to function right without restarts...

---

