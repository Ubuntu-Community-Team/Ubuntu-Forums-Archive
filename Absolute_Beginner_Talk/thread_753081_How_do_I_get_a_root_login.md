---
title: "How do I get a root login?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-12
Hello

on this subject of accounts and logins...

am i correct to say that to do a root login from the desktop....you get a terminal window and type

sudo login

then type your username and then your password?

thanks

Vince.

---

### Post by aysiu on 2008-04-12
If you want a semi-permanent root login, the command would be ```
sudo -i
``` and then your user password.

---

### Post by vinceUUUU on 2008-04-12
Hello 

thanks for that....does semi permanent mean it would stop after i turn off that linux session and the PC?

thanks

Vince.

---

### Post by tamoneya on 2008-04-12
it means that it will only have root permissions for one command```
sudo apt-get update
ls ~
``` In this case apt-get update will have root access while ls ~ will not.

---

### Post by hyper_ch on 2008-04-12
it stops after a while...

but definitively if you end the session

---

### Post by aysiu on 2008-04-13
> **vinceUUUU said:**
> Hello 

thanks for that....does semi permanent mean it would stop after i turn off that linux session and the PC?

thanks

Vince.
*Semi-permanent* means you would be root until you type the command ```
exit
```

---

