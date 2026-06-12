---
title: "Ubuntu 5.10, GAIM keeps closing out"
date: 2008-06-03
forum: Apple Hardware Users
---

### Post by UnsafeData on 2008-06-03
IRC was no help (thanks alot guys). I'm using an iMac G3.

GAIM 1.0.5 or so keeps closing out when I login. I removed my account, readded it and it worked... then closed out after a while (not too long). I reinstalled it using my disc two times, which didnt work so that's not an option.

I don't know what to do.

---

### Post by cyberdork33 on 2008-06-03
run gaim from the terminal and it should give you a better message as to why it is crashing.

Also, why are you still on 5.10?

---

### Post by UnsafeData on 2008-06-03
I'm going to upgrade to Dapper today.. since it's still supported til 2009 and all. Not sure if newer versions of Ubuntu works well on this but I've been told in the IRC that Dapper works well. The latest versions of Ubunutu don't have ppc versions, which is bad news for me and my iMac here. :(


ANYWAYS I RAN IT FROM THE TERMINAL:


*** glibc detected *** free(): invalid pointer: 0x0f13cb7c ***
Aborted



So there it is. I dont know what that is.

---

### Post by cyberdork33 on 2008-06-03
> **UnsafeData said:**
> The latest versions of Ubunutu don't have ppc versions, which is bad news for me and my iMac here. :(there are newer releases, including the latest, 8.04. Check the PPC FAQ stickied in this forum.

I would guess that your error is due to an older version of glibc.

---

### Post by UnsafeData on 2008-06-03
> **cyberdork33 said:**
> there are newer releases, including the latest, 8.04. Check the PPC FAQ stickied in this forum.

I would guess that your error is due to an older version of glibc.

Okay I'll read the sticky. and yeah i figured that would be the case here.

---

