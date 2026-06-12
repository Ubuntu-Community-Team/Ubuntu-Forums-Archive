---
title: "cannot boot studio properly. it,s like trying luck out"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by sarojgupta on 2008-03-24
Hi, I'm completely new to ubuntu. I want to update my softwares on ubuntu studio 7.10. it keep comin g error as need to run  configure --dpkg -a manually. now, what is dpkg? and where do i need to go and how can i do it.? also got another major problem that is i've dual booted ubuntu studio 7.10 with win xp. I have to boot my computer may be 10 times in order to actally boot into ubuntu 7.10. can anyone suggest me as to how to boot properly without having to switich on and off many many times ! thanxs

---

### Post by wolfen69 on 2008-03-24
go to applications>accessories>terminal
copy and paste the following:
```
sudo dpkg --configure -a
```

---

### Post by prshah on 2008-03-24
> **sarojgupta said:**
> Hi, I'm completely new to ubuntu. I want to update my softwares on ubuntu studio 7.10. it keep comin g error as need to run  configure --dpkg -a manually. now, what is dpkg? and where do i need to go and how can i do it.? also got another major problem that is i've dual booted ubuntu studio 7.10 with win xp. I have to boot my computer may be 10 times in order to actally boot into ubuntu 7.10. can anyone suggest me as to how to boot properly without having to switich on and off many many times ! thanxs

You can try to extend the GRUB timeout by opening a terminal and ```
sudo gedit /boot/grub/menu.lst
```, then locate the line STARTING with the word "timeout" (No # before the word) and change it to 20. Then save and exit, and when back at the terminal, type ```
sudo update-grub
```

Next time you boot, you will have 20 seconds to select Windows or Ubuntu.

---

