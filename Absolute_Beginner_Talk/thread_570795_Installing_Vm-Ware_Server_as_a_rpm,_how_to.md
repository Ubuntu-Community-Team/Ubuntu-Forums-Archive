---
title: "Installing Vm-Ware Server as a rpm, how to?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-10-08
I want to install it from an rpm because it wont work in the tar.gz. . . So I get this in the terminal what do I do?```
tito@TITOS-LAPTOP:~$ cd Desktop
tito@TITOS-LAPTOP:~/Desktop$ sudo alien -i VMware-server-1.0.4-56528.i386.rpmWarning: Skipping conversion of scripts in package VMware-server: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.

```

??? What do I do next?

---

### Post by ~~Tito~~ on 2007-10-08
It made  DEB on my desktop but i cant run it cause the permissions are root's, I AM ROOT WTF. . . How do I change this?

---

### Post by FuturePilot on 2007-10-08
Do what it says. Add the --scripts flag into the command
```
sudo alien -i --scripts VMware-server-1.0.4-56528.i386.rpm
```
Without it it may not work right. Those are post install scripts it needs to run and without the --scripts flag it won't convert them and therefore will not run them either.

---

### Post by ~~Tito~~ on 2007-10-08
Will Post what happens.```
tito@TITOS-LAPTOP:~/Desktop$ sudo alien -i --scripts VMware-server-1.0.4-56528.i386.rpm
mkdir: cannot create directory `VMware-server-1.0.4': File exists


```

Where do I delete that folder so I can start over.

---

### Post by ~~Tito~~ on 2007-10-08
Oh, its on the desktop but IT WONT LET ME DELETE!!!! Says access denied.

---

### Post by FuturePilot on 2007-10-08
Use a root nautilus.
```
gksudo nautilus
```

---

