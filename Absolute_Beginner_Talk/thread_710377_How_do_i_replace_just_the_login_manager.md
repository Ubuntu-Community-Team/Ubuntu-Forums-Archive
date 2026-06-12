---
title: "How do i replace just the login manager?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2008-02-28
I want to use remote login using XDMCP but it is broken in GDM. SOmeone said i should replace the login manager with KDM.
How do i do this but still keep gnome as my desktop environment?

---

### Post by wolfen69 on 2008-02-28
```
sudo apt-get remove gdm
```
```
sudo apt-get install kdm
```

---

### Post by dgrafix on 2008-02-28
Thanks,

Done that but the setup for login window has disappeared. Im figuring i need the equivalent for gdmsetup for kdm so i can enable XDMCP.

---

