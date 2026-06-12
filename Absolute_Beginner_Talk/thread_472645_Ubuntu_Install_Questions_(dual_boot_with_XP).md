---
title: "Ubuntu Install Questions (dual boot with XP)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by BillyB on 2007-06-13
I'm rebuilding my laptop (again!) and want to dual boot XP & Ubuntu. I had a previous installation with XP plus a 2GB system + 256MB swap for Ubuntu which instantly ran out of disk space! Which is why I'm starting over..

How much space should I allow for a working version of Ubuntu (at the moment I'm mostly learing so shouldn't need to much space for data files). My laptop has a 19GB drive.

Second question, at my last attempt I used Symantec BootMagic but after my Ubuntu install I ended up with GRUB instead. It wasn't a problem but I'd like to know if I should just forget BootMagic or if there is a way to use it instead of GRUB.

Thanks in advance.

---

### Post by Cypher on 2007-06-13
you'd want to dedicate at least 6GB to Ubuntu, unless you're very careful about what programs you install for testing/playing around and remove them after you're done to not take up too much space. 

By default, the Ubuntu installer will install GRUB on the MBR and overwrite any other boot-loader you have. To prevent that, you can ask the Ubuntu installer to install GRUB on the parition in which Ubuntu is installed instead. This will keep your current boot-loader intact and you'll have to take some extra steps to make Linux boot.

I have no clue how BootMagic works, so I can't even begin to tell you how you'd make it boot Ubuntu..

---

### Post by starcraft.man on 2007-06-13
> **Cypher said:**
> you'd want to dedicate at least 6GB to Ubuntu, unless you're very careful about what programs you install for testing/playing around and remove them after you're done to not take up too much space. 

By default, the Ubuntu installer will install GRUB on the MBR and overwrite any other boot-loader you have. To prevent that, you can ask the Ubuntu installer to install GRUB on the parition in which Ubuntu is installed instead. This will keep your current boot-loader intact and you'll have to take some extra steps to make Linux boot.

I have no clue how BootMagic works, so I can't even begin to tell you how you'd make it boot Ubuntu..

Agreed with cypher. 6 GB is my recommended minimum. I also hope you have decent ram in it if your just using 256 Swap, I recommend at least 512... unless you have multiple GBs of ram in there or don't do much.

As for BootMagic, thats the third party boot loader that comes with partition magic right? Man, that suite IMO gone down hill. I remember when it wasn't owned by symantec and it was perfect, Symantec just keeps buying out products I love and turning them into bloated crappy products (they did same to sygate my favourite windows firewall, that became their bloated one).

Don't use boot magic please... I don't think its that good and we shouldn't encourage Symantec to continue ruining my (and other peoples) favourite companies. If you need a partitioner, I recommend gparted and you can get it and a few other system utilities on this [system disk.]("http://www.sysresccd.org/Main_Page").

---

