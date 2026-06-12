---
title: "Gaim 2"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-21
Trying to install Gaim 2 but I get this:

```

simon@ubuntu:~$ sudo apt-get install gaim2.0 Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gaim2.0: Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1 is to be installed
           Depends: libdbus-1-2 (>= 0.60) but it is not installable
           Depends: libdbus-glib-1-2 (>= 0.60) but it is not installable
           Depends: libglib2.0-0 (>= 2.8.5) but 2.8.3-0ubuntu1 is to be installed
           Depends: libpango1.0-0 (>= 1.10.2) but 1.10.1-0ubuntu1 is to be installed
           Depends: libxrender1 (>= 1:0.9.0.2) but 1:0.9.0-1 is to be installed
E: Broken packages
simon@ubuntu:~$

```

Not sure what I need to do now?

---

### Post by AndrewCaul on 2006-03-21
Uninstallable dependencies? I seem to be having that problem. I also can't get APT to read a few of my repositories.
Do you have all the necessary repositories enabled?

---

### Post by NeghVar on 2006-03-21
i think it has to do with breezy/dapper, all the instructions regard dapper which has those, breezy is a step behind on them

---

### Post by tmahmood on 2006-03-21
hello? gaim2 is not out yet. so how come you get it through repositories?

---

### Post by NeghVar on 2006-03-21
its beta

---

### Post by _simon_ on 2006-03-21
i'll stick with 1.5 then for now :)

---

### Post by krusbjorn on 2006-03-21
[QUOTE=tmahmood]hello? gaim2 is not out yet. so how come you get it through repositories?[/QUOTE]

Add this line to your /etc/apt/sources.list

> deb [http://idefix.eup.uva.es/paquetes/gaim2.0/](http://idefix.eup.uva.es/paquetes/gaim2.0/) ./

---

### Post by dicecca112 on 2006-03-24
that doesn't work same error

---

