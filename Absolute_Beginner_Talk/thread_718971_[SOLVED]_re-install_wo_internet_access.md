---
title: "[SOLVED] re-install w/o internet access"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by chesch on 2008-03-08
Hello all,

I am in the process of re-installing Gutsy Gibbons on a computer that doesn't have internet access with a fresh install.  Last time I did that, a friend of mine pointed me to a file that I had to un-comment out a few lines so that I could do updates over the internet

Can anyone point me to the file so that I can do that again (once I get ubuntu installed and internet access again)?

-Chesch

---

### Post by wormser on 2008-03-08
You need to edit /etc/apt/sources.list.  A GUI way is System> Administration> Software Sources.

---

### Post by chesch on 2008-03-08
thank you very much!

---

### Post by freelinuxhelp on 2008-03-08
It should prompt you to get updates automatically after installation if you have Internet access.

It sounds like your friend might have had you edit the sources file. If that's the case, you can edit it with this command:  gksudo gedit /etc/apt/sources.list

Or you could go to System -> Administration -> Software Sources.

---

