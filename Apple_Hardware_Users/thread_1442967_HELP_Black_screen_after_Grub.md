---
title: "HELP: Black screen after Grub"
date: 2010-03-30
forum: Apple Hardware Users
---

### Post by jzhou2oo6 on 2010-03-30
HELP! I have just finished a fresh install of ubuntu 9.10 on Macbook 5,2 triple boot system. I boot up the system. i select Linux in the EFI boot loader 0.14 i have windows 7and Mac os snow leopard 10.6.2. i select ubuntu in the Grub boot loader afterwards i select linux in the EFI bootloader. I get a black screen afterwards with a flashing curser at the top right corner

---

### Post by linuxopjemac on 2010-03-30
have a look here:
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

### Post by jzhou2oo6 on 2010-03-30
No go although it is a black screen no flashing cursor

---

### Post by linuxopjemac on 2010-03-31
In Grub: Hit F6 to change the boot options ,then disable acpi enter:
```
acpi=off
```
in the boot line. Some people also added:
```
noapic nolapic irqpoll vga=771
```
If you don't want to loose acpi functions you can add this other option:
```
maxcpus=1 
```

---

