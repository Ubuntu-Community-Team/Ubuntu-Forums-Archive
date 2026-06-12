---
title: "[SOLVED] What happens when 7.10 is released?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2007-08-30
I'm currently running 7.04 and am happy with my setup but I have also carefully documented all my changes.

**My question** is what will happen this October when I want to upgrade to the completed release of 7.10? 

Will my system automatically upgrade via the update manager or will I need to burn a whole new live CD and install it?

I also don't have a separate home partition, will this make for issues? (I have an external hard drive so I could easily backup and replace on the home.)

Thanks.

---

### Post by abhilash82 on 2007-08-30
This thread gives you the option of upgrading your kernel to Gutsy from Feisty.
[http://ubuntuforums.org/showthread.php?t=511974&page=19](http://ubuntuforums.org/showthread.php?t=511974&page=19)

---

### Post by farueulogy on 2007-08-30
Thanks for the information - But will it be the same procedure when 7.10 is actually released?

---

### Post by stevebakerj on 2007-08-30
I would just use Synaptic or Adept to upgrade from Feisty to Gusty when its released. Not having a separate /home partition wont cause any problems but it might be worth researching how to move your home contents onto a separate partition prior to the upgrade so you can use it to take advantage of having a separate /home partition. You have got 2 months so you could practice using virtual setups in VirtualBox.

Good luck

---

### Post by por100pre1 on 2007-08-30
> **farueulogy said:**
> I'm currently running 7.04 and am happy with my setup but I have also carefully documented all my changes.

**My question** is what will happen this October when I want to upgrade to the completed release of 7.10? 

Will my system automatically upgrade via the update manager or will I need to burn a whole new live CD and install it?

I also don't have a separate home partition, will this make for issues? (I have an external hard drive so I could easily backup and replace on the home.)

Thanks.

First, you don't have to anything in October, it not required to upgrade at that time. You can upgrade running when ready:

```
gksu update-manger -d
```

The best way, however, is to download a Gutsy disk to install when you get ready. It's a good idea to backup your files in an ext HDD all the time. Grsync makes it easy. :)

---

### Post by Kobalt on 2007-08-30
When Ubuntu 7.10 will come out (supposedly on the 18th of October) the update manager should offer you the possibility to upgrade simply by clicking "Upgrade to the newer version". 
However, creating a separate /home partition is an advice I regularly and strongly give away. In case your upgrade goes bad, you don't lose your personal data and settings. If you feel Ubuntu 7.10 is slow after the upgrade (which might happen in some cases) and you want a fresh install, again you can keep your personal data and settings... It's the same if you want to install another distro. 
If you decide to make a separate /home partition, here is [a good procedure]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by por100pre1 on 2007-08-30
> **Kobalt said:**
> When Ubuntu 7.10 will come out (supposedly on the 18th of October) the update manager should offer you the possibility to upgrade simply by clicking "Upgrade to the newer version". 
However, creating a separate /home partition is an advice I regularly and strongly give away. In case your upgrade goes bad, you don't lose your personal data and settings. If you feel Ubuntu 7.10 is slow after the upgrade (which might happen in some cases) and you want a fresh install, again you can keep your personal data and settings... It's the same if you want to install another distro. 
If you decide to make a separate /home partition, here is [a good procedure]("http://www.psychocats.net/ubuntu/separatehome").

Thanks for the corrections Kobalt. :)

---

### Post by be4truth on 2007-08-30
> **Kobalt said:**
> When Ubuntu 7.10 will come out (supposedly on the 18th of October) the update manager should offer you the possibility to upgrade simply by clicking "Upgrade to the newer version". 
However, creating a separate /home partition is an advice I regularly and strongly give away. In case your upgrade goes bad, you don't lose your personal data and settings. If you feel Ubuntu 7.10 is slow after the upgrade (which might happen in some cases) and you want a fresh install, again you can keep your personal data and settings... It's the same if you want to install another distro. 
If you decide to make a separate /home partition, here is [a good procedure]("http://www.psychocats.net/ubuntu/separatehome").

Congratulations for your 2000th bean!

---

### Post by Kobalt on 2007-08-30
lol thanks !

---

