---
title: "How Can I Remotely Access Windows XP Machine in Ubuntu?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by SamMessing on 2006-09-01
I am still new to Ubuntu, and run Windows XP on my desktop (Ubuntu on my laptop). I have been able to remotely access my laptop (Ubuntu) using the Windows machine, and now want to do the reverse. Can anyone suggest to me a way to do remotely acces a Windows XP machine from Ubuntu?

Sorry if this question is somewhat obvious, I've looked around but can only find stuff about accessing Ubuntu from Windows Xp, not the other way around.

Thanks!
Sam

---

### Post by aysiu on 2006-09-01
Maybe try TightVNC?

---

### Post by Cyraxzz on 2006-09-01
VNC is installed by default.

---

### Post by eentonig on 2006-09-01
Is RDP available on the Windows machine? If so, it's a lot faster to use the RDP protocol to access the Windows machine from your Ubuntu. I'm not a MS fan, but when they make something good, I have to admit it.

Application\Internet\Terminal Server client

---

### Post by bodhi.zazen on 2006-09-01
I agree with eentonig.

You have to configure your XP box to accept the connection (default is to reject).

---

### Post by wieman01 on 2006-09-01
Or simply install a **SSH server** on the Windows machine. Then you should have full access Windows although only through a terminal. 

TightVNC is a good option as well if you need a graphical interface. Have used it before.

---

