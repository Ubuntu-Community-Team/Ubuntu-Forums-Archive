---
title: "Administration"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by tenwesta on 2006-12-27
How could i give administration privilegies to some other user. I did it i nano editor (visudo) and i gave him the privilegies. But it still doesnt work, do i have to do something else????? THNX

---

### Post by taurus on 2006-12-27
Just add his login name to both groups adm & admin in /etc/group...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/group
```
p.s.  And don't forget to remind him that he can trash the whole system if he doesn't watch what he is doing with the sudo!

---

