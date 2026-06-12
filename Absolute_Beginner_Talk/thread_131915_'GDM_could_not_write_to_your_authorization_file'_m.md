---
title: "'GDM could not write to your authorization file' message"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by iffy9 on 2006-02-17
When I try to log on, I am getting the following message:

'GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator.'

What do I do now?

TIA

Ian

---

### Post by ScreemingBlue on 2006-02-17
Use CTRL-ALT-F1 to get to a terminal session and if your username is Tony try entering...

> sudo chown -R Tony /home/Tony

Use CTRL-ALT-F7 to get back to your gdm and try login again.

---

### Post by iffy9 on 2006-02-17
Tried that, still get the same message.  What next?

TIA

Ian

---

### Post by iffy9 on 2006-02-17
Managed to delete some files from my HDD.  I will have to get the hang of this mounting lark.  I have a 20GB HDD that I can't see or add files too!!

Thanks anyway.

Ian

---

