---
title: "su login?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by levigruber on 2006-07-19
I am trying to install a .deb file, which is glGo, a program to play Go online. When I try to open it with GDebi, the default program, in order to install, it says(of course), that I lack the permission to run or open the file. I changed the permissions, so I could execute the program, but no go. It makes sense that installing programs would require your password, but it does'nt ever even ask me for mine. I tried to log in through the terminal several times, but there is no asterisks or dots for the characters in the password, and I put in my password five times very carefully, but it does'nt recognize it. Help!](*,)

---

### Post by meng on 2006-07-19
In my experience, the easiest way to install from .deb file is:
```
sudo dpkg -i nameofdeb.deb
```
Use your regular user password when asked for password.
EDIT: There won't be any asterisks/dots echoed to screen when entering password.

---

### Post by levigruber on 2006-07-20
Thanks a bunch.

Levi-

---

### Post by Madpilot on 2006-07-20
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) will explain how Ubuntu handles sudo/su/admin privs - it's slightly different from the way some other distros handle things.

*Edit for dumb typo*

---

