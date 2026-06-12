---
title: "Sudo without password question"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by philosophia on 2006-09-01
I have been following ubuntuguide.org on how to enable system users to use sudo without having to enter a password.  I used visudo to add this line to /etc/sudoers

system_username         ALL=(ALL)       NOPASSWD: ALL

it doesn't seem to have worked.  When I run sudo I'm still prompted for my password.  After I enter my password once, I'm not prompted for it again, however.  If I kill sudo, I have to reenter my password.

What am I doing wrong?

---

### Post by nazgulord on 2006-09-01
I don't recommend that you make it so that you don't have to enter a password for sudo. It makes your system less secure.

nazgulord.

---

### Post by philosophia on 2006-09-01
why is this not working though?

---

### Post by kerry_s on 2006-09-01
try this> %admin ALL=NOPASSWD: ALL

---

