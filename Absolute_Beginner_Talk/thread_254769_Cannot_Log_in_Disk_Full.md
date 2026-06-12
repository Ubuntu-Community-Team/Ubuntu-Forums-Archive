---
title: "Cannot Log in Disk Full"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by ut1205 on 2006-09-10
Hi All
This is my first encounter with Linux and everything worked fine untill I installed a couple of new games.  Pop up window said "Disk Full" during installation but gave me no option to stop it.  Now when I try to log in it says "Disk Full" not possible to log in.
I would like to uninstall and start again since I know a little more about what I am doing now but I can find no evidence on any of my drives that anything was installed, however, it runs without the CD installed.
I rebooted with the CD and it just loads the OS and doesn't give me any chance to change or edit anything.

How do I go back and start all over again?

Thanks in advance for your help.:D

---

### Post by Najand on 2006-09-10
> **ut1205 said:**
> Hi All
This is my first encounter with Linux and everything worked fine untill I installed a couple of new games.  Pop up window said "Disk Full" during installation but gave me no option to stop it.  Now when I try to log in it says "Disk Full" not possible to log in.
I would like to uninstall and start again since I know a little more about what I am doing now but I can find no evidence on any of my drives that anything was installed, however, it runs without the CD installed.
I rebooted with the CD and it just loads the OS and doesn't give me any chance to change or edit anything.

How do I go back and start all over again?

Thanks in advance for your help.:D

Can you push ALT+CTRL+F1 and log in Command Mode?
You should also do:
```
sudo apt-get clean
```
to clean your apt cache to open some space.

---

### Post by bulldog on 2006-09-10
When you boot from the live cd you aren't actually using your hdd but your cd-rom.
You can try however if you can mount your Ubuntu install and remove some stuff using your live cd to boot.

sudo mkdir /mnt/ubuntu
sudo mount /dev/hd?? /mnt/ubuntu [where hd?? stands for your ubuntu partition]

---

