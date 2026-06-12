---
title: "Error when installing SLAB through automatix"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Charco on 2006-11-23
Here is the error output.

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-main-menu: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages

!!SCRIPT OUTPUT END!!
[11/23/2006 - 09:23.18] - ERRORS OR WARNINGS WHERE REPORTED
[11/23/2006 - 09:23.18] - FATAL - Slab - An apt-based error occured and installation was unsuccessful
[11/23/2006 - 09:26.03] - !!Starting Automatix 1.1-1.10!!
[11/23/2006 - 09:26.07] - Updated keys with 3B2EA15A
[11/23/2006 - 09:26.08] - Updated keys with DD4D5088
[11/23/2006 - 09:26.27] - !!SCRIPT OUTPUT START!!


```

Is there a way to fix this? Thanks in advance.

---

### Post by skit on 2006-11-27
I have the exact some problem, it is asking for the libdbus-1-2 package even thought i have libdbus-1-3 installed.

If someone could please solve this.

---

### Post by Charco on 2006-11-28
Ok, I just downloaded the deb file for libdbus-1-2 and installed it. Everything works after that!

Deb found here:
[http://packages.ubuntulinux.org/dapper/devel/libdbus-1-2](http://packages.ubuntulinux.org/dapper/devel/libdbus-1-2)

---

