---
title: "Package conflicts ?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Dalenaa on 2008-03-28
Hello :)  i am pretty new to Ubuntu but have slight experience, i am trying to install the axigen Mail server on to my Ubuntu 7.10 Server edition server.
However i nubishly install the mail server option for the server additon and it is now interfering with my installation of the Axigen Mail Server Program.

When i type in the install command for Axigen. Dpkg -1 axigen_6.0.0-1_i386.deb. 
It returns and error message saying that :" Postfix conflicts with mail-Transport-agent" conflicting packages. . I cant figure out how to remove the original mail server package. 

Anything helps =D thank you!

Dalenaa

---

### Post by Oldsoldier2003 on 2008-03-28
> **Dalenaa said:**
> Hello :)  i am pretty new to Ubuntu but have slight experience, i am trying to install the axigen Mail server on to my Ubuntu 7.10 Server edition server.
However i nubishly install the mail server option for the server additon and it is now interfering with my installation of the Axigen Mail Server Program.

When i type in the install command for Axigen. Dpkg -1 axigen_6.0.0-1_i386.deb. 
It returns and error message saying that :" Postfix conflicts with mail-Transport-agent" conflicting packages. . I cant figure out how to remove the original mail server package. 

Anything helps =D thank you!

Dalenaa

```
apt-get purge postfix
```

---

### Post by Dalenaa on 2008-03-28
Thank you so much :-D!!

worked like a carm

<3

---

