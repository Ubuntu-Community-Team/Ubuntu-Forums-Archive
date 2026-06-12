---
title: "samba problems, windows cant access ubuntu"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-04-11
ok as the title says im having some samba problems

i have no samba users file, or password file
and my 2 windows computers cant access my ubuntu install over the network, but my ubuntu install can access my windows computer

also my modded xbox can access my shares to play my movies over the network.. what should i do? am i missing a package?

oh is there a way i can make it fully open? i mean my folders are set to public also, but i cant even access the computer to view the folders

---

### Post by joshrobinson on 2006-04-11
found my problem

smbpasswd -a USERNAME

solved it

---

