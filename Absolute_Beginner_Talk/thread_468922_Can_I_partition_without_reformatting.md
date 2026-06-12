---
title: "Can I partition without reformatting?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Dryvlyne on 2007-06-09
I've been running on Ubuntu for about 2 months now and have come to realize that it would have probably been a good idea for me to partition my drive at the time of installation. Is there any way I can partition the drive without reformatting?

Thanks

---

### Post by Kobalt on 2007-06-09
What kind of partitioning do you want to do exactly ?

---

### Post by ghost_ryder35 on 2007-06-09
hell yea:)  Gnome Partition Editor, you might have to sudo-apt get it or use the add/remove feature to get it!  but you can defintly do that

---

### Post by Dryvlyne on 2007-06-09
> **Kobalt said:**
> What kind of partitioning do you want to do exactly ?
Thanks for the reply.

I'd like to rearrange my filesystem. For example, I'd like a separate partition for /usr and a separate one for /boot and so on.

Thanks

---

### Post by Kobalt on 2007-06-09
You can use Gparted to resize a partition and make several others... Though if I were you I'd backup and reinstall it all. Then I'd specify the partitions and their mount points to the installer. I'd find it 'cleaner' than resizing and repartitioning from the existing scheme, then editing manually fstab...

---

### Post by Dryvlyne on 2007-06-09
> **Kobalt said:**
> You can use Gparted to resize a partition and make several others... Though if I were you I'd backup and reinstall it all. Then I'd specify the partitions and their mount points to the installer. I'd find it 'cleaner' than resizing and repartitioning from the existing scheme, then editing manually fstab...
Thanks for the advice. Perhaps I'll just wait until the next release as I don't really want to reinstall all of my apps right now.

BTW, do you have any recommendations on how I should partition a new installation when I'm ready to do that?

I was looking at the following documentation which outlines the common directories under the root directory and I didn't know if it's preferred to have each of those directories on their own partition or not.

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/directories-file-systems.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/directories-file-systems.html)

Thanks

---

### Post by Kobalt on 2007-06-09
If you have an old machine, then it can be usefull to separate the /boot folder onto its own partition. But if the machine you have is rather recent (within 3 years I'd say) then my advise would be to have a separate /home partition. It's the essential : you keep your personnal data out of the applications and systems files, so that if you want to add another Linux distro or if you mess up you current installation, if you want to resintall your system : you don't loose your personnal datas and settings. It can be done really easily, from the Live CD directly. But you can also do it without a whole reinstall. See [this]("http://psychocats.net/ubuntu/separatehome") for more info.
For other folders you can put some on a separate partition as well, but this is more of an advanced user need.

---

### Post by Dryvlyne on 2007-06-09
> **Kobalt said:**
> If you have an old machine, then it can be usefull to separate the /boot folder onto its own partition. But if the machine you have is rather recent (within 3 years I'd say) then my advise would be to have a separate /home partition. It's the essential : you keep your personnal data out of the applications and systems files, so that if you want to add another Linux distro or if you mess up you current installation, if you want to resintall your system : you don't loose your personnal datas and settings. It can be done really easily, from the Live CD directly. But you can also do it without a whole reinstall. See [this]("http://psychocats.net/ubuntu/separatehome") for more info.
For other folders you can put some on a separate partition as well, but this is more of an advanced user need.
Thank you for the link Kobalt, I will try this later. It appears to be exactly what I was looking for. Regards

---

### Post by Kobalt on 2007-06-09
You're welcome.

---

