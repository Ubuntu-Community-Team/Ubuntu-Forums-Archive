---
title: "Windows XP and ubuntu on the same PC"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Athlon1600 on 2007-11-12
If i install ubuntu on the seperate drive, would it work?

---

### Post by ubnewbie2 on 2007-11-12
> **Athlon1600 said:**
> If i install ubuntu on the seperate drive, would it work?

Yes.  Ubuntu will see that you have XP already installed - will even offer to try to migrate user accounts, and it will add XP to the list of options at boot time, so you can choose which system you wish to start using.  just be sure to tell Ubuntu to install to the correct place (not over the top of XP :-))

 It will also be able to mount any ntfs drive/partitions you have and use them for storage. (plus there is an installable file system for XP that will let you access the Ubuntu drive/partition when in XP.

---

### Post by Athlon1600 on 2007-11-12
ok thanks for information

---

### Post by htmlguy on 2007-11-12
Google "Wubi" Its a program that lets you run XP and Ubuntu and is great for beginers.

---

### Post by aysiu on 2007-11-12
If you have more than 512 MB of RAM, I'd recommend using VirtualBox to install Ubuntu inside of Windows.

This approach has several advantages: [list][*]You don't have to worry about accidentally deleting your hard drive. [*]There's a lot less of a chance your computer won't be able to boot any OS, in case something goes wrong with the boot loader. [*]If there are problems (sound not working, internet working), Windows is immediately available to fall back on. You do not need to reboot to switch OSes. [*]You don't have to burn a CD. You can install Ubuntu in a virtual drive straight from the disk image.[/list]

---

