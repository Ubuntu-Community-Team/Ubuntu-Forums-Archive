---
title: "/var/lib/dpkg/lock"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by SimonM on 2007-06-23
I have been trying to install using makefiles, I know in order to do this you have to update and build aptitude etc, However, whenever I run any commands relating to aptitude I am receiving this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Any advice would be appriciated

Simon

---

### Post by bapoumba on 2007-06-23
> **SimonM said:**
> I have been trying to install using makefiles, I know in order to do this you have to update and build aptitude etc, However, whenever I run any commands relating to aptitude I am receiving this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Any advice would be appriciated

Simon
Do you have another package manager running ? (only one can run at a time, there is a lock file to handle this).

But I do not understand: "you have to update and build aptitude".

---

