---
title: "[SOLVED] Can not load menu editor."
date: 2008-02-24
forum: Arch and derivatives
---

### Post by perlluver on 2008-02-24
I tried to open up menu editor and alacarte, for it to tell me, that I do no in fact own my ./config/menus.  I tried to chown them, but that didn't help either.  Anyone have any suggestons?

---

### Post by PurposeOfReason on 2008-02-24
Did you also chmod 775 them? I've had this problem with my whole home directory before with every file. Doing chown -R USERNAME /home/USERNAME.

---

### Post by Rumor on 2008-02-24
You have to run alacarte as root.

---

### Post by perlluver on 2008-02-24
I just made a new account, I couldn't add new sessions or anything.  Thanks for the help though.

---

### Post by alex_anthony on 2008-03-02
> **Rumor said:**
> You have to run alacarte as root.
lies!
running alacarte as user changes the users menu just fine
same on every other distro - you don't see it asking for root password anywhere else do you

---

