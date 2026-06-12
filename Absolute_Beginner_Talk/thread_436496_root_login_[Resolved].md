---
title: "root login? [Resolved]"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-05-07
how do i login as root? i need to replace a file in usr/share/pixmaps/

i tried to log out and use my current pass but no go?

---

### Post by aysiu on 2007-05-07
You don't need to log in as root.

This will help you:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by Happy_Man on 2007-05-07
In ubuntu, the root account is locked. To execute a command as root, use the prefix "sudo." for example, to edit your file, simply enter:

```
sudo gedit /usr/share/pixmaps/file.ext
```

---

### Post by aysiu on 2007-05-07
Use *gksudo* for graphical applications, not *sudo*. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by silent1643 on 2007-05-07
is there not anyway to make my current account have all the rights as a root account per my password auth..

or a file browser that will elminate the terminal need to do this?

---

### Post by aysiu on 2007-05-07
> **silent1643 said:**
> is there not anyway to make my current account have all the rights as a root account per my password auth..

or a file browser that will elminate the terminal need to do this?
Yes on both counts! Read the link I posted earlier:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by drowner on 2007-05-07
> **silent1643 said:**
> is there not anyway to make my current account have all the rights as a root account per my password auth..

or a file browser that will elminate the terminal need to do this?


I dont think you want to log in as root. You might think you do, but you dont, trust me.

---

### Post by Happy_Man on 2007-05-07
> **drowner said:**
> I dont think you want to log in as root. You might think you do, but you dont, trust me.

Tru dat! I tried other Linux distros before coming to Ubuntu, wanted SOOO badly to stay with Sabayon or Arch, but eventually decided on Ubuntu _*just because of sudo*_. You have NO idea how great it is.

---

### Post by silent1643 on 2007-05-07
> **aysiu said:**
> Yes on both counts! Read the link I posted earlier:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

perfect, now i feel like i run this computer again :D

---

### Post by silent1643 on 2007-05-07
> **Happy_Man said:**
> Tru dat! I tried other Linux distros before coming to Ubuntu, wanted SOOO badly to stay with Sabayon or Arch, but eventually decided on Ubuntu _*just because of sudo*_. You have NO idea how great it is.

why can't i use the graphical interface but have it prompt for a password whenever try to do something only sudo should be able to do ..?

---

