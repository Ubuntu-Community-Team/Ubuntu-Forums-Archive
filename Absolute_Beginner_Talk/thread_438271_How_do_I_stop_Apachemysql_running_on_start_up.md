---
title: "How do I stop Apache/mysql running on start up?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by readitsideways on 2007-05-09
Hi

I have Apache2 and mysql installed, but they start at startup and I only need them running when I'm developing. I know I can start and stop them in the services manager, but I'd rather not have to stop them every time I turn the system on. How do I stop them running at startup?

Regards

Duncan

---

### Post by Inxsible on 2007-05-09
Go to
System –> Preferences –> Sessions -> Startup Programs 
 
and simply delete the entries for Apache and MySQL.

---

### Post by mazirian on 2007-05-09
Wow, I can't beleive there's a GUI for this now.  I use:

```

update-rc.d foo default # adds a service to the default runlevel
update-rc.d foo remove # removesd a service from the default runlevel

```

So update-rc.d apache2 remove should do the trick.

---

### Post by readitsideways on 2007-05-10
Thanks

---

### Post by GavinZac on 2007-10-13
> **Inxsible said:**
> Go to
System –> Preferences –> Sessions -> Startup Programs 
 
and simply delete the entries for Apache and MySQL.

neither mysql nor apache2 are listed there.

---

### Post by mysurface on 2007-10-13
I do the manual way. By running runlevel, i know the run level is 2..
so i go to 
/etc/rc2.d

I change the unwanted service symlink from S***** to K****, for examples:

sudo mv {S,K}91apache2

---

