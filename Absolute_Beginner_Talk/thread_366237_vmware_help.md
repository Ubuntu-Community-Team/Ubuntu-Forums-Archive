---
title: "vmware help"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-20
i installed vmware server using this tutorial: 
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

it installed ok, but when i run it from: system tools>vmware server console
i get
Failed to execute child process "vmware" (No such file or directory)

also, i tried starting it from the terminal and i get:
bash: vmware: command not found

or with sudo

sudo: vmware: command not found

:confused: :confused:

---

### Post by aktiwers on 2007-02-20
It doesnt look like you installed it currect?
Did you get through the part where you have to type in your Serial number?

---

### Post by panti19 on 2007-02-21
yes

it said it completed successfully

---

### Post by veloce on 2007-02-21
Did you run vmware-config?

---

### Post by PetePete on 2007-02-21
try 
```

sudo updatedb
locate vmware

```

see if its been installed anywhere

have you patched your kernel to support the vmware modules? 
(this gets done when you run the configuration script after the install)

---

### Post by djearwig on 2007-03-27
type this into the command line to start VMware:
/etc/init.d./vmware start

---

