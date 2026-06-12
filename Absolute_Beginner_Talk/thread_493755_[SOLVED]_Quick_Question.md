---
title: "[SOLVED] Quick Question"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-07-06
Is there a way to dissable the password prompt when opening an app?

It gets really annoying because how often I use my computer.


Thanks!

---

### Post by felicity on 2007-07-06
What application(s) are you referring to when you say it requires a password when opening it?

---

### Post by phizikal on 2007-07-06
Synaptic, Terminal, Add/Remove. such...

---

### Post by H3g3m0n on 2007-07-06
Edit /etc/sudoers as root (ie 'gksudo gedit'), change:

%admin ALL=(ALL) ALL

to

%admin ALL=NOPASSWD: ALL

This is in theory a major security risk as a program can now gain root access by just using sudo (assuming its run as an admin user) which would be a way for spyware or malicious code to get into the system, but most people will run things blindly as root anyway and there probably isn't anything out there that would use sudo to get in.

Your also suposed to use 'visudo' to edit the file to ensure that you don't screw it up, but visudo is a version of vim a terminal text editor which isn't easy to use, although if you learn it its very powerful. If you know vim then use visudo instead.

---

### Post by phizikal on 2007-07-06
Thanks man. That helps.

---

