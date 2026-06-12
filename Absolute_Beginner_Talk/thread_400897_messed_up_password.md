---
title: "messed up password"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2007-04-04
I wanted to change my password so I used the command sudo passwd -d  and now I have no password.  How can I give myself a new password?

---

### Post by amohanty on 2007-04-04
Any particular reason you used sudo?

Does using **passwd** as is to setup a password work???

AM

---

### Post by jbumgar on 2007-04-04
after the -d I typed in xxx

---

### Post by amohanty on 2007-04-04
So what happens if you just type:
**passwd**
as the regular logged in user? Can you set a password.

AM

---

### Post by jbumgar on 2007-04-04
If I type passwd nothing happens.  No I don't know how to recreate a new password and that is what I need to know how to do.

---

### Post by amohanty on 2007-04-04
Can you use the System-Administration->Users.. tool to reset the password?

or try: **passwd username**


AM

---

### Post by jbumgar on 2007-04-04
passwd username did it.  Many thanks for your help!

Jim
-------

---

