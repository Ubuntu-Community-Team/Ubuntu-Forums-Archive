---
title: "Cannot boot ubuntu from a partition. 2011 Mactel 13.1&quot;"
date: 2013-08-25
forum: Apple Hardware Users
---

### Post by yhjung012 on 2013-08-25
Hello people! I am running into bit of problem here.

I have a 2011 Mactel in which I installed a 2nd HDD using a optibay. That I initially installed Windows 7 using boot camp. I decided to install Ubuntu on then 2nd HDD via USB and I was successful. Initially after installation GRUB 2 would run fine and I can boot Ubuntu. I would hear the MAC boot up sound and it ubuntu GRUB2 would run. However, recently that is not running automatically and I cannot access the partition. The MAC disk utility reads the partition but says it can't be mounted (so I can't boot from MAC bios from pressing "option" key) and when I press F2 (boot option for windows) to access the the ubuntu partition, but it doesn't read the partition. Help?

---

### Post by Elfy on 2013-08-26
*Thread moved to **Apple Users**.*

---

### Post by SilverOne on 2013-08-26
hi,

if you wish to autoload grub you'll have to bless it;  if however you wish to choose on boot, you'll need an additional boot loader known as refind. 

you can find information on the bless method here: [https://wiki.archlinux.org/index.php/MacBook#Using_blessing]("https://wiki.archlinux.org/index.php/MacBook#Using_blessing")
you can download and install refind from here: [http://www.rodsbooks.com/refind/]("http://www.rodsbooks.com/refind/")

---

### Post by yhjung012 on 2013-08-27
Thank you, I will check it out!

---

