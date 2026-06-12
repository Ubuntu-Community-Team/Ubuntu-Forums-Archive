---
title: "clean /var/cache/apt/archives"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by hackxxcrack on 2007-09-13
Hi i want to clean /var/cache/apt/archives archives but when i use 

sudo apt-get clean the archives are still there...

how can i clean them? and another cuestion how can i delete archives from terminal...

thank you

---

### Post by llamakc on 2007-09-13
"sudo apt-get clean" and "sudo apt-get autoclean" work fine for me from the terminal, and removed all of the archives.

---

### Post by hackxxcrack on 2007-09-13
ok

how can i delete archives from terminal?

thanks

---

### Post by llamakc on 2007-09-13
sudo apt-get clean

---

### Post by hackxxcrack on 2007-09-13
NO i mean any archive like if i have Hello.tar.gz in my desktop how can i delete it from terminal...

---

### Post by Maestro23 on 2007-09-13
> **hackxxcrack said:**
> NO i mean any archive like if i have Hello.tar.gz in my desktop how can i delete it from terminal...


Your post title and what you are asking to do are not the same.

> rm filename

> rm -r directory

In terminal you can type:

> man rm (Tells the syntax of the command).

---

