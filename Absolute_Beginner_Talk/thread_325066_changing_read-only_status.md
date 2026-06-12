---
title: "changing read-only status?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by calebjohnson77 on 2006-12-24
I am wanting to change my source list, so that I can update my apt-get files ... but I am encountering a problem.  When I go to the file:  /etc/apt/sources.list and try to modify it, the file has been set up as a read-only file.  I couldn't go into the file and change the permissions on it, because it claims that I am not the owner.  Is there a way to override this?

---

### Post by spockrock on 2006-12-24
ok the reason why its only read-only is because you need root privileges to modify it.
doing this in terminal will allow you to do so,

sudo gedit /etc/apt/sources.list

---

### Post by MkfIbK7a on 2006-12-24
exatly what distro are you running if dapper gnome open a terminal and type
gksudo nautilus

---

### Post by MkfIbK7a on 2006-12-24
this opens a root nautilus

acctually a sudo nautilus

---

### Post by NeoLithium on 2006-12-24
Either of those ways work well; just don't change the permissions on the sources.list; it being permissioned the way it is, prevents any accidents happening with your list of sources. :)

---

### Post by MkfIbK7a on 2006-12-24
> It being permissioned the way it is, prevents any accidents happening with your list of sources.
Absolutely correct!

---

