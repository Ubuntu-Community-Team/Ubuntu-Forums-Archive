---
title: "Copy Ubuntu HD to Bigger HD"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by JohnPta on 2008-03-30
I have in my computer two hd hd0 and hd1.
Hd0 has windows on it and the boot loader for Windows/Ubuntu. The size is 80Gb
Hd1 has Ubuntu. The size is 20Gb.

Now I want to copy/Ghost the content of the 20Gb HD to the 80Gb HD.
However there could be a problem: When I take out the Hd0 there is no bootloader anymore and therefore it will NOT see Ubuntu. 
How can I solve that problem?

---

### Post by sancho panza on 2008-03-30
Before removing the drives, login to ubuntu and install grub, which gets installed on the drive with ubuntu on it. Then I guess you should be able to see ubuntu. But am not sure how the copying of the Ghost onto the other drive would turn out with grub. ie, am not sure if grub will see windows.

PS: my bad, I mixed up the two drives while reading the post. sorry.

---

### Post by logos34 on 2008-03-30
Grub is on hd0, but points to /boot/grub/menu.lst on the linux root on hd1. Therefore what you want to do is reinstall grub after you copy ubuntu from the smaller to larger hdd.  But make sure beforehand to edit menu.lst and /etc/fstab to point to the new drive/partition(s).

---

### Post by bumanie on 2008-03-30
Are you planning to get rid of windows altogether and have an ubuntu only computer? It is important to know whether you want windows or not.

---

### Post by JohnPta on 2008-03-30
> **sancho panza said:**
> Before removing the drives, login to ubuntu and install grub, which gets installed on the drive with ubuntu on it. Then I guess you should be able to see ubuntu. But am not sure how the copying of the Ghost onto the other drive would turn out with grub. ie, am not sure if grub will see windows.

PS: my bad, I mixed up the two drives while reading the post. sorry.

But how do I install Grub or an other package in the Second HD, in my case the Ubuntu HD? 
When I can boot from HD1 (Ubuntu) than I am a happy chappy..

---

### Post by JohnPta on 2008-03-30
> **logos34 said:**
> Grub is on hd0, but points to /boot/grub/menu.lst on the linux root on hd1. Therefore what you want to do is reinstall grub after you copy ubuntu from the smaller to larger hdd.  But make sure beforehand to edit menu.lst and /etc/fstab to point to the new drive/partition(s).

How can I reinstall Grub when I can not get into my Ubuntu HD? In other words: How can I copy Grub onto the Ubuntu HD and what must I change to address Ubuntu properly?
Can I make bootable floppy disk and install Grub that way?

---

### Post by JohnPta on 2008-03-30
> **bumanie said:**
> Are you planning to get rid of windows altogether and have an ubuntu only computer? It is important to know whether you want windows or not.

I still have two or three software packages which I use in Windows e.g. a Geovision Surveillance System Which unfortunately only works under windows and I need that package for security camera's. So I want to move the Ubuntu to the big HD and reformat that small HD and put windows on that.

---

### Post by Duck2006 on 2008-03-30
You will need to reinstall grub, this may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

