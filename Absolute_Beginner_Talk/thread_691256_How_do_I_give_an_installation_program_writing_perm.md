---
title: "How do I give an installation program writing permission"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-08
Hi there,

i am about to install DOOM 3 , it's going to install itself into /usr/local folder which is protected. It asks me to give my root password but that is not enough. How do I run it (from the terminal) so that it has the necessary privileges and how to I change the in the terminal to the cdrom0 device etc, please instruct me on every step, i don't knowmuch about terminal lines.

Thanks for your support in the phanastic forum
Andreas

---

### Post by papuccino1 on 2008-02-08
Are you installing in Wine?

---

### Post by Djalmahal on 2008-02-08
No, wine is not involved, it is for linux, with shell scripts and such

---

### Post by Djalmahal on 2008-02-08
I found these instructions, but they don't work as such,it tell's me "Can't open .....", is they path wrong?

1) sh /mnt/cdrom/doom3-linux-1.1.1282.x86.run

2) cd /usr/local/games/doom3

3) tar -xjvf /mnt/cdrom/files-1.tar.bz2

Unmount the first disk/image and then mount the second one

4) tar -xjvf /mnt/cdrom/files-2.tar.bz2

Unmount the second disk/image and then mount the third one

5) tar -xjvf /mnt/cdrom/files-3.tar.bz2

Any comments?

---

