---
title: "How to run programs I just installed"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Indiana Red on 2006-12-23
OK, I have 6.10 w/o the gui and am using putty from my XP box on the same lan.
I am working on getting it on the existing domain and understand I need Samba.  I think I did it right so far:
apt-get -f install samba 
I think it D/Ld it OK, but I have a more fundamental problem.  With all these things I am getting, Apache, Samba, etc, how do I run them or use them.  How to see or confirm that they are not ony there...but running and working.  I have nothing to "double-click" and I don't have a "task-bar" to see what is running.
i am missing something here..
Help Please.

---

### Post by dbbolton on 2006-12-23
you need to edit this file:
```
sudo gedit /etc/samba/smb.conf
```

for help, see:

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

