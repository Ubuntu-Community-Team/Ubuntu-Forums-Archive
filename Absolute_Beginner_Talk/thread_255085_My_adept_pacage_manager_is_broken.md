---
title: "My adept pacage manager is broken"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-10
My Adept package manager doesn't work any more. It gives the message below. How can I fix it?

Details: Failed to execute child process "kdesu" (No such file or directory)

---

### Post by Najand on 2006-09-10
> **jbumgar said:**
> My Adept package manager doesn't work any more. It gives the message below. How can I fix it?

Details: Failed to execute child process "kdesu" (No such file or directory)

Can you run the following?
> /usr/bin/kdesu adept

---

### Post by jbumgar on 2006-09-10
Nope it says:   /usr/bin/kdesu adept
bash: /usr/bin/kdesu: No such file or directory

---

### Post by Najand on 2006-09-10
Can you do
```
ls -la /usr/bin/kde*
```
and see if the command is available or not? If it is not find it using:
```
locate kdesu
```

---

### Post by jbumgar on 2006-09-11
Nope says this: jim@jim-desktop:~$ ls -la /usr/bin/kde
ls: /usr/bin/kde: No such file or directory

---

### Post by Najand on 2006-09-11
Do you have kde installed? I mean are you using kubuntu or "defualt ubuntu with gnome"?

---

### Post by jbumgar on 2006-09-11
default ububtu dapper.  Should I try to find kdeadept?

---

