---
title: "/etc/security/limits.conf: Permission denied"
date: 2011-12-19
forum: Apple Hardware Users
---

### Post by john amino on 2011-12-19
so....i'm slowly getting the hang of this

but

i need to get JACK running in realtime mode and to do that i need to edit /etc/security/limits.conf.

however Permission Denied

how do i get permission?

---

### Post by rsavage on 2011-12-20
If you want to edit a file that is owned by 'root' then the best way to do this is using the sudo/gksudo commands from the terminal.

Type 

```

gksudo gedit /etc/security/limits.conf

```

to open the graphical text editor with root permission.

---

### Post by john amino on 2011-12-20
thank you very much

this forum has been the most helpful i've come across, you're a credit to the internet :D

merry christmas

---

### Post by rsavage on 2011-12-21
Wow!  Thanks, that is very kind.  I was feeling quite low yesterday, but you really cheered me up with this message!  Happy christmas to you too!

---

