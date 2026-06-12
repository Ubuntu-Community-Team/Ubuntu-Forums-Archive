---
title: "Is there a way to lock programs?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-26
Hi, every once in a while I let my little brother on my computer. He, being used to windows, has no clue where anything is and sometimes winds up messing with things that I don't want him messing with, such as music and other files. Is there a way I can lock things such as Limewire and Amarok, and Automatix, or things like that? I really don't want to make a whole new user profile just so he can get on the computer every week or so.

---

### Post by taurus on 2006-11-26
You can create an account for him to use except use a restricted shell like /bin/rsh!  You can specify what commands he can run while he logs in...

```
man rsh
```

---

### Post by AnimalMother on 2006-11-26
"gpg" (GNU Privacy Guard) Check out its man page. very simple to use and it will work for you.

in a terminal type:
```

man gpg

```
***_BUT..._***

EVEN THOUGH YOU DON'T WANT TO, make a new user for him and just restrict access to anybody but you for any given program. It will be simpler and faster than encrypting everything you don't want him touching.  It would be simpiler to download an Ubuntu live cd (Or KNOPPIX, or Morphix...) and just boot that up for him to use instead of encrypting.  Never let anyone use your login unless it is your mother and she is not on needle drugs.

---

### Post by indigoshift on 2006-12-21
> **AnimalMother said:**
>  Never let anyone use your login unless it is your mother and she is not on needle drugs.

Oh, look.  My new sig.

Thanks!  ;) :D

---

### Post by steve.horsley on 2006-12-21
I give my young monster his own account. He can do what he pleases in there, and at the very worst, I'll have to wipe anc recreate his account if he screws it completely.

---

### Post by az on 2006-12-21
> **voodoonirvana said:**
> I really don't want to make a whole new user profile just so he can get on the computer every week or so.

Why not?  It is pretty much trivial to do, and it is meant to accomplish exactly what you need to do.

---

