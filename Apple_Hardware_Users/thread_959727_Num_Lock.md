---
title: "Num Lock"
date: 2008-10-26
forum: Apple Hardware Users
---

### Post by Deadpool on 2008-10-26
I have a Macbook, and a lot of the time the num lock randomly turns on. Because the keyboard isn't right, I can't turn it off either by pressing the num lock key, or by using the num lock button on xvkbd. Thanks for any help you can give me.

---

### Post by cyberdork33 on 2008-10-26
try F6 (likely Fn+F6 for you)

---

### Post by hictio on 2008-10-26
Perhaps this: [Enabling NumLock during startup and before login](https://help.ubuntu.com/community/NumLock) might come handy too.

maybe this works on the Apple version as well, I mean, setting up like this:
```

numlockx off

```

instead as on the doc, where they provide the info to have on.

---

### Post by Deadpool on 2008-10-27
> **hictio said:**
> Perhaps this: [Enabling NumLock during startup and before login](https://help.ubuntu.com/community/NumLock) might come handy too.

maybe this works on the Apple version as well, I mean, setting up like this:
```

numlockx off

```

instead as on the doc, where they provide the info to have on.

It looks like it would, but the file is read-only, and using sudo edit (or open) Default is spouting out errors.

---

### Post by hictio on 2008-10-27
Sorry, I don't understand you... Yes, the '/etc/gdm/Init/Default' is read only for a regular user, you can edit like this:

```

gksudo gedit /etc/gdm/Init/Default

```

It'll prompt you for your password.

---

### Post by Deadpool on 2008-10-27
> **hictio said:**
> Sorry, I don't understand you... Yes, the '/etc/gdm/Init/Default' is read only for a regular user, you can edit like this:

```

gksudo gedit /etc/gdm/Init/Default

```

It'll prompt you for your password.

Thanks, if it works, I'll thank you formally

---

### Post by hictio on 2008-10-27
That's fine, but you read the doc I linked on my first post right?
You need to install a program, 'numlockx' and then edit the configuration file, so it is executed when the graphical logins starts.

---

