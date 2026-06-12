---
title: "Bootings problems"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Krishnan on 2007-10-18
Hi. From the last 2 days iam facing this problem where my ubuntu fails to enter the boot list. I am only able to see my other os i.e. win Xp. Ubuntu Fails to boot. I have tried to enable the grub using the live cd with the following commands
Sudo Grub
Find /boot/grub/stage1
root (hd1, 6)
Setup(hd0)
Quit
       After following all these steps. It says that it has succeeded but when i restart i fail to get my ubuntu on
the boot list
Please provide me the solution

---

### Post by overdrank on 2007-10-18
> **Krishnan said:**
> Hi. From the last 2 days iam facing this problem where my ubuntu fails to enter the boot list. I am only able to see my other os i.e. win Xp. Ubuntu Fails to boot. I have tried to enable the grub using the live cd with the following commands
Sudo Grub
Find /boot/grub/stage1
root (hd1, 6)
Setup(hd0)
Quit
       After following all these steps. It says that it has succeeded but when i restart i fail to get my ubuntu on
the boot list
Please provide me the solution

HI and I assume the system booted to ubuntu at one time? Did this start not booting after updates?  You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and then hit enter and then  b to boot. So you can see any errors during boot.  Hope this helps. Good luck!

---

### Post by Krishnan on 2007-10-18
Buddy I dont see Ubuntu Kernel at all in the boot list. I am only able to get Windows Xp. Its only through the live cd i can go to Ubuntu.

---

### Post by ajgreeny on 2007-10-18
> Its only through the live cd i can go to Ubuntu.What do you mean exactly by this?  Are you using the live CD itself, or does it somehow allow you to boot into your installed version on the hard disk?

Let's have a look at your output from ```
sudo fdisk -l
``` from the live CD.

---

### Post by Krishnan on 2007-10-18
Its is only when i put my live cd. I can get through the installed files and folders of ubuntu. Otherwise i can't boot.

---

### Post by ajgreeny on 2007-10-18
As I said, let's see your output from ```
sudo fdisk -l
```and also what are the contents of your /boot/grub/menu.lst file on the installed ubuntu, not the live CD (actually, there isn't one on the live CD).

---

### Post by Krishnan on 2007-10-25
I have a 200 Gb Hd.  I use two os. Winxp and ubuntu. Please view the attachments where i have given my output

---

### Post by Krishnan on 2007-10-25
plz help

---

