---
title: "Dual Boot DVD drive disappear FIXED!"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by vonchiz on 2008-01-24
I am running a dual boot win XP and Ubuntu install.  The problem I was having was that my CD/DVD drive disappeared when I installed grub. The only boot loader that would allow the drive to display in the OS was windows or 3rd party boot loaders that would render Linux unbootable. It was a bear to fix, but here's how I did it.  I couldn't get anyone to help,  so I'm posting this to help others that might have the same problem so they don't have to figure it out on their own.

From what I could tell, grub doesn't play nice with some removable laptop drives (the majority seem to be Clevo models, like my own).   I tried several 3rd party boot loaders and either the problem replicated or Grub wouldn't boot linux.

Step 1. Replace Grub with Lilo as loutlined here
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)
I used the apt-get option to install Lilo on an already running partition that booted from Grub, the directions are good.
MAKE SURE you install Lilo on your Ubuntu partition and not on your MBR.

Step 2. Install GAG as my bootloader. Very straightforward. Linux won't boot if you have your bootloader installed on your MBR.  

After doing all this, my problem went completely away.

If you know how to install grub on your linux partition and not MBR, it would work also. I got sick of #($%ing around with it and switched to Lilo.  I almost gave up on using Linux outside a live CD, but have really been impressed and have enjoyed it since I got it working.

Hope this helps, and you can enjoy Ubuntu as much as I have.

---

### Post by brettg on 2008-01-29
Yep, had the exact same problem with a Clevo laptop, had to fix it the same way. If you don't want to run Windows at all you can also workaround the problem by using grub with the acpi=off directive but then you lose all acpi funcionality. 

Such a pita, as I'm sure you have discovered.

---

