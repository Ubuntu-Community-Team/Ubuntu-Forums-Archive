---
title: "[SOLVED] Help needed with su password..."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by AndrewS on 2008-02-01
Hi

Probably a silly question, but is my "su" password different from the administrator password (e.g. the one I use to use synaptic etc)?

Thanks

Andrew

---

### Post by jan quark on 2008-02-01
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lswest on 2008-02-01
yes, su and sudo -s require the password of your root account (username: root) as you're logging in as the root user in that case, whereas sudo and gksudo (the password prompt when opening administrative tasks) require the password of your current user (e.g. mine's lswest).

---

### Post by Bachstelze on 2008-02-01
> **lswest said:**
> yes, su and **sudo -s** require the password of your root account (username: root)

Wrong. Anything *sudo* takes the password of the user running it, that's the whole point...

EDIT : and by the way, *sudo -s* is a very bad idea, please always use *sudo -i*.

---

### Post by billgoldberg on 2008-02-01
No, on my pc it's the same.

If I do "sudo su" in the terminal I enter the admin password.

---

### Post by AndrewS on 2008-02-01
Many thanks, that helped a lot.

Andrew

---

### Post by Bachstelze on 2008-02-01
> **billgoldberg said:**
> No, on my pc it's the same.

If I do "sudo su" in the terminal I enter the admin password.

That's exactly what I'm saying! As long as it begins with *sudo*, it takes the password of the user running it. Period.

---

### Post by lswest on 2008-02-01
haha, could be, i wasn't sure, only ever use sudo [command] :P

---

