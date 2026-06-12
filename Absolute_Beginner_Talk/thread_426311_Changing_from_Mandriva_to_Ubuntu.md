---
title: "Changing from Mandriva to Ubuntu"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-04-28
I jumped into converting from Vista to Linux to quickly and have installed Mandriva 2007 on my brand new laptop without doing any research into other distributions. I dual booted it with Windows MCE 2005. I am thinking of changing from Mandriva to Ubuntu Feisty Fawn and am wondering how I would do it and if it would mess up the bootloader that Mandriva have installed. Once I uninstall Mandriva will my computer just boot windows normally before i install ubuntu. Any help I would be grateful, thankyou!

---

### Post by sailor2001 on 2007-04-28
no..... mandriva installed it's own boot loader, windows requires (by itself) MBR. However with the ubuntu disk, it has it's own bootloader (grub) that works with windows and most all distributions..If you want to restore windows bootloader, get to your dos windows and "fixmbr"

---

### Post by AlexenderReez on 2007-04-28
i'm using vista ultimate dual boot with ubuntu...i realized that vista also has its own 'grub loader '...but as mandriva using gfxboot ...i don't think you can straight boot to windows after remove mandriva partition(i don't sure because i never try ) ...but i really suggest that after you remove mandriva straightly install ubuntu...whatever

   [SIZE="4"][COLOR="Blue"] 'welcome to the world of king of distribution '[/COLOR][/SIZE]

---

### Post by thecomputingexpert on 2007-04-28
is it possible to just install ubuntu over mandriva, or format the mandriva partition during ubuntu installation and then install ubuntu.

---

### Post by vanadium on 2007-04-28
In my opinion, you should be able to run the Ubuntu setup and specify custom partitioning. This loads the graphical partitioning utility, where you can either reformat your Mandriva partition, or delete it and create a new one. You can leave the Mandriva swap partition in place and use it for Ubuntu. The Ubuntu install program will configure grub based on what it finds on your partitions, i.e. a windows partition and a linux partition (unless you messed up during the partitioning, of course).

Following my approach is easier, though. Just wipe your Windows partition. After two weeks, you won miss it anymore ...

---

