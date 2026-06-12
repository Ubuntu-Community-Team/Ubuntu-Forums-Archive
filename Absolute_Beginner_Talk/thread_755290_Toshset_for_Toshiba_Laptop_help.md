---
title: "Toshset for Toshiba Laptop help"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-04-14
```
tom@Laptop:~$ toshset
toshset: can't get I/O permissions.
        Please run as root.
tom@Laptop:~$ sudo toshset
required kernel toshiba support not enabled.
tom@Laptop:~$ 

```

What do I do now?

---

### Post by lundholmj on 2008-04-14
sudo modprobe toshiba or / and sudo modprobe toshiba_acpi

---

### Post by Tom--d on 2008-04-14
```
tom@Laptop:~$ sudo modprobe toshiba
FATAL: Error inserting toshiba (/lib/modules/2.6.22-14-generic/kernel/drivers/char/toshiba.ko): No such device
tom@Laptop:~$ sudo modprobe tosihba_acpi
FATAL: Module tosihba_acpi not found.
tom@Laptop:~$ 
tom@Laptop:~$ 

```

I guess it never worked :\

---

### Post by Toshibawarrior on 2008-06-23
I have the same problem as Tom...is there any way to fix this on a Toshiba Satellite A135 S4527?.........Please!

---

