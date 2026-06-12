---
title: "need help with admin rights"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by pentium on 2006-09-01
I recently got a copy of ubuntu 5.10 and proceeded to install it. After I was done with the install I attempted to log in as "root", which it seems has all the rights to the system. For some reason I can only logon as root through the non-graphical environment. I created a second account "john" during the install but it seems that it needs to be allowed by root to run most of the admin programs. Because I don't know a thing about the ubuntu command system, How can I get root to give all access privelages to john?

On another note, Where can I get a serial terminal program that allows for me to run a diagnostic terminal through a serial port  and can I use a serial mouse instead of a ps/2 or usb mouse?

---

### Post by taurus on 2006-09-01
You don't log in as root directly; instead, you use sudo to run root's commands from a regular user, the first user that you created during the installing process...

```

sudo <command>
(use the same password that you use to log in...)

```

---

### Post by Abstract on 2006-09-01
> **taurus said:**
> You don't log in as root directly; instead, you use sudo to run root's commands from a regular user, the first user that you created during the installing process...

```

sudo <command>
(use the same password that you use to log in...)

```

Also note if you are running a graphical program from the terminal use gksudo instead of sudo.

```

gksudo <graphical command>
(use the same password that you use to log in...)

```

If you ever need a root console, dont login as root. Do this:

```

sudo -i

```

---

### Post by pentium on 2006-09-01
I can see the program starting up but then suddenly it closes.

---

### Post by Bachstelze on 2006-09-01
Which program ?

---

### Post by taurus on 2006-09-01
What program are you talking about?  Wanna share with us!!!

---

### Post by pentium on 2006-09-01
All of the programs under the admin menu (excluding device manager) are having this problem.

---

### Post by Bachstelze on 2006-09-01
What happens if you run them manuallly ? Like e.g. Alt+F2, gksudo network-admin ?

If it still doesn't work... Well, be positive and consider it a nice opportunity to learn how to manage your system from command-line :)

---

### Post by taurus on 2006-09-01
Perhaps you don't have the right permission, belonging to the right group, to use sudo!!!  What is the output of this command from a terminal then?

```
id
```

---

### Post by pentium on 2006-09-01
> Alt+F2, gksudo network-admin 

That gives me lots-o-drive use followed by nothing
I can't even run root terminal!

---

### Post by taurus on 2006-09-01
What groups do you belong to???

```
id
```

---

### Post by pentium on 2006-09-01
didn't see the last post.
uid=1000(john) gid=1000(john) groups=4(adm), 20(dialout), 24(cdrom), 25(floppy), 29(audio), 30(dip), 44(video), 46(plugdev), 104(lpadmin), 105(scanner), 1000(john)

---

### Post by pentium on 2006-09-01
do you also want me to id root while I am still here?

---

### Post by pentium on 2006-09-02
have I been forgotten?

---

