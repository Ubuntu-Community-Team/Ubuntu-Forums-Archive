---
title: "Add Users Via Terminal"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2006-01-18
Like the title says... How can i?

Thanks
~Lance

---

### Post by paulmilliken on 2006-01-18
[QUOTE=noob_Lance]Like the title says... How can i?

Thanks
~Lance[/QUOTE]
Either "useradd" or "adduser" should do the trick.  Type "man useradd" and "man adduser" for details.

---

### Post by noob_Lance on 2006-01-18
that worked... now how can i make them stuck to a certail dir and that dir only??

---

### Post by paulmilliken on 2006-01-18
[QUOTE=noob_Lance]that worked... now how can i make them stuck to a certail dir and that dir only??[/QUOTE]
Check that a directory "/home/newusername" hasn't already been created automatically.  Also, can you please post the exact command that you ran to add the new user.

---

### Post by noob_Lance on 2006-01-19
the users DIR was created, and i used sudo adduser to d a new user

---

