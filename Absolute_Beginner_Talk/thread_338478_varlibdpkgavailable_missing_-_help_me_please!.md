---
title: "/var/lib/dpkg/available missing - help me please!"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Laracna on 2007-01-14
I'm trying to install a package, but everytime I try to install any package I've got this error message: 

```

dpkg: failed to open package info file '/var/lib/dpkg/available' for reading: No such file or directory
E; subprocess /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover

```

I don't know what ot do. It's the first time i'm using linux and it's only 2 days i've installed Ubuntu 6.06 Dapper here.

I'll apreciate any help!

---

### Post by riven0 on 2007-01-14
Alright, open the terminal and try this:

> sudo dpkg --configure -a


What does it give back?

---

### Post by Laracna on 2007-01-15
It gave me back:

```

dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

```

---

### Post by riven0 on 2007-01-15
How about creating a folder there?:
> 
sudo mkdir /var/lib/dpkg/available

then running:

> sudo dpkg --configure -a

---

### Post by Buck2348 on 2007-01-15
/var/lib/dpkg/available is a text file.

---

### Post by Laracna on 2007-01-16
The folder /var/lib/dpkg existis, but the file available don't.

I already tryied to create available file, but it always gives me back the same message error. :(

---

### Post by riven0 on 2007-01-16
If it's an actualy file, you may want to try copying it from the liveCD. Boot it up, mount your hd, and just copy it from there. 

Otherwise, re-installing dpkg may help this, but the first option seems less error proof.

---

