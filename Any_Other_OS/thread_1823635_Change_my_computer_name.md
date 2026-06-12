---
title: "Change my computer name"
date: 2011-08-12
forum: Any Other OS
---

### Post by chaituchill on 2011-08-12
Hi,

Can somebody please tell me how to change my computer name 

its coming up as chaitu@linuxmint~$ on my terminal.... i want to change it to something like chaitu@computername~$  .....i tried hostname command but in vain...

Thanx.

Bye,
Chaitu

---

### Post by realzippy on 2011-08-12
```
gksudo gedit /etc/hostname
```

..here it works.
Btw,welcome to UF!


...maybe you ask in the linux mint forum if it not works.

---

### Post by deserthowler on 2011-08-12
I haven't done that for a while but you might need to change the file /etc/hosts too.

Earl

---

### Post by CatKiller on 2011-08-12
deserthowler ++

If you don't change them both, sudo stops working.

You used to be able to do it in the GUI with the networking tool, but it's a feature that hasn't made it into NetworkManager yet.

---

### Post by Perfect Storm on 2011-08-12
Moved to Other OS/Distro Talk.
Note that Linux Mint have their own forum at [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by chaituchill on 2011-08-19
tried it did change the prompt on my terminal to chaitu@<newhostname> but when i restarted my computer again it still shows "chaitu@linuxmint$:" in my terminal ..." linuxmint is the original computer name...however it showed 

 Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

when i tried the gksudo gedit /etc/hostname... and after i changed the hostname in file tried to save it

Thanks

---

