---
title: "how do you switch partitions to run windows/linux"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by DillPill on 2006-08-03
Hello, I have windows XP on one partition and ubuntu on the other. How do I switch it to run linux instead of it booting up windows everytime? thanks

---

### Post by ColdDeath on 2006-08-03
> **DillPill said:**
> Hello, I have windows XP on one partition and ubuntu on the other. How do I switch it to run linux instead of it booting up windows everytime? thanks

Hello DillPill,

When Ubuntu installs, it will also install a tool called GRUB. GRUB is what is known as a boot loader, it will allow you to choose between a list of operating systems that are  defined in grub.conf.

Did you install Windows after Ubuntu? Because that would cause it to overwrite GRUB in the MBR (Master Boot Record).

If you have, don't worry too much, you can install GRUB again. But its always best to install Windows first as it isn't as friendly as Ubuntu ;)

---

### Post by DillPill on 2006-08-03
First, thanks for the quick responce. Second, I installed windows AFTER ubuntu..so where can I find this grub, how do i work it? thanks

---

### Post by zxee on 2006-08-03
> **DillPill said:**
> Hello, I have windows XP on one partition and ubuntu on the other. How do I switch it to run linux instead of it booting up windows everytime? thanks

When you did the install did you choose to not install grub?
You can use the install/livecd to install grub now but more info is needed to help you with that. From the livecd do fdisk -l in a terminal and post the output.

---

### Post by aysiu on 2006-08-03
> **DillPill said:**
> First, thanks for the quick responce. Second, I installed windows AFTER ubuntu..so where can I find this grub, how do i work it? thanks
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

