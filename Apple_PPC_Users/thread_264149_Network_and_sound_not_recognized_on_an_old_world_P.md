---
title: "Network and sound not recognized on an old world PowerBook G3"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by Jimmy_r on 2006-09-24
I have installed dapper on an old world PowerBook G3.
Network and sound are not recognized, are there any specific kernel modules or something to load? I dont really know what else information to give, so just tell me what you need to know :)

---

### Post by Jimmy_r on 2006-09-24
It was probably a badly formulated question, but my head was nearing the boiling-point at the time...

Anyway, i managed to fix it. For reference:

I added to /etc/modules:
dmasound_pmac  #For sound

bmac   #for ethernet

pmac_zilog  #for internal modem

---

### Post by Ptero-4 on 2006-11-17
jimmy. Have you tested your internal modem? Does it get past the "EXPECT (OK)" in the ppp log (which you access tipyng plog in a shell)?

---

