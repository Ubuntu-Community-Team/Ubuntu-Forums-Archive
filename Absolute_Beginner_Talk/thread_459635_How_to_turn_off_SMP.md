---
title: "How to turn off SMP"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by HumpbackInTheBay on 2007-05-30
I have installed Feisty on my Dell Optiplex 745(dual core x86) and was happy everything works great. Although by default the kernel installed is 2.6.20-15-generic #2 SMP, I would like to try installing the non-SMP version of the same kernel. I went through forum posts and then did :
apt-get install linux-686 and
apt-get install linux-headers-686
expecting that it would get the non-SMP linux-686 version as one of the options on booting.
However, I rebooted only to find that my kernel is still the SMP version.

Could someone point me how I can turn switch to the 686 non-SMP version.

Thanks in advance

---

### Post by testube_babies on 2007-05-30
I don't know why you would want to do this, but i believe the linux-386 kernel won't use SMP.

---

### Post by yabbadabbadont on 2007-05-30
You will need to edit your /boot/grub/menu.lst file (you will have to use sudo) and add "nosmp"  (without the quotes) as an option on the "# defoptions=" line.  Then run "sudo update-grub".  (without the quotes)

---

### Post by stchman on 2007-05-31
> **HumpbackInTheBay said:**
> I have installed Feisty on my Dell Optiplex 745(dual core x86) and was happy everything works great. Although by default the kernel installed is 2.6.20-15-generic #2 SMP, I would like to try installing the non-SMP version of the same kernel. I went through forum posts and then did :
apt-get install linux-686 and
apt-get install linux-headers-686
expecting that it would get the non-SMP linux-686 version as one of the options on booting.
However, I rebooted only to find that my kernel is still the SMP version.

Could someone point me how I can turn switch to the 686 non-SMP version.

Thanks in advance

You paid for a multi core processor, so why would you want to not use the other core?

Ubuntu is SMP capable so use it.

---

