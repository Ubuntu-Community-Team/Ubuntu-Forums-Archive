---
title: "editing kernel [edit terminal too]"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Heretic on 2006-06-24
I want to edit my terminal so instead of saying "mctoasted-desktop", it says localhost. During the install it didnt ask me what I wanted. I read somewhere you can edit the kernel to accomplish this. How?

[img]http://img66.imageshack.us/img66/4097/desktop4up.jpg[/img]

---

### Post by David_T on 2006-06-24
You should be able to change your computer name by going to System > Administration > Networking and then on the General tab, changing the contents of the Hostname field, then rebooting.  If you otherwise want to change your terminal prompt, you'll need to edit your .bashrc file in your home directory to assign some other value to PS1.

---

