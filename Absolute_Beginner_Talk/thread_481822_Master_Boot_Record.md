---
title: "Master Boot Record?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by viseversa on 2007-06-22
After installing Ubuntu the screen where I select which O/S to run(I believe its the master boot record) has to many options, about 4 of them are all for loading Ubuntu. How can I change it?

---

### Post by Happy_Man on 2007-06-22
It's called GRUB. You can edit that list by editing the file /etc/apt/sources.list. Although, it is typically advised against unless you know what you are doing.... what's the problem with it?

---

### Post by viseversa on 2007-06-22
I just wanted to remove the other 3 Ubuntu's from the list because theres 4.

---

### Post by Happy_Man on 2007-06-22
There really is no need to, they won't hurt and if you run into problems with the current kernel, you can boot an earlier one to fix it. Quite useful.

---

### Post by Seisen on 2007-06-22
> **Happy_Man said:**
> It's called GRUB. You can edit that list by editing the file /etc/apt/sources.list. Although, it is typically advised against unless you know what you are doing.... what's the problem with it?

You put down the wrong location to edit the file, its /boot/grub/menu.lst. 

viseversa, I would leave them alone because two of them are recovery mode in case you have a problem with kernel or something and the other one is you other kernel.

---

### Post by Happy_Man on 2007-06-23
> **Seisen said:**
> You put down the wrong location to edit the file, its /boot/grub/menu.lst. 

viseversa, I would leave them alone because two of them are recovery mode in case you have a problem with kernel or something and the other one is you other kernel.
*sighs* Dang, you're right. I ALWAYS GET THOSE MIXED UP!!!! No idea why. Perhaps I should start writing lines: "etc/apt/sources.list is for repos, /boot/grub/menu.lst is for GRUB. /etc/apt/sources.list is for repos...."

---

