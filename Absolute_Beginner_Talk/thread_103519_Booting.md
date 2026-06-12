---
title: "Booting"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2005-12-14
Hello!
I have a very simple question: I have installed Baltix linux once, and after that it wasn't possible to boot windows. There was no option for it in the boot menu. Then, I installed Mandriva linux and I have dual booting now - I can choose win or linux.
So, if I install Ubuntu, will there be dual-booting or will it just be Ubuntu?

---

### Post by M3ta7h3ad on 2005-12-14
It should detect your operating systems on your system and set it up for dual boot :)

---

### Post by anil_robo on 2005-12-14
Ubuntu does allow multisystem boot. When installing, you have to delete one of your other partitions to make some space for Ubuntu. Also, make sure you check for all the other OS in the list before writing GRUB to boot record. I boot in Ubuntu and WinXP.

---

### Post by Herman on 2005-12-14
The Ubuntu install CD has its own partitioner which can install Ubuntu on any free space on your hard disk if any is spare.

 If there isn't, you can use the Ubuntu partitioner to take some space from a WIndows partition if there is unused space in it and it has been well defragged first. 

The Ubuntu partitioner, as far as I know, will not re-size another Linux partition, you can delete it and install Ubuntu in it's place if necessary. That depends on how badly you want Ubuntu, and whether you have any other choices available to get some free space somewhere.

The best boot loader for Ubuntu is GRUB, and you can boot lots of operating systems with it, I don't know how many the limit is. If you are worried about it, you can also make yourself a GAG bootloader floppy disk for emergency use, but I doubt if you will have to use it. GRUB is a good boot loader. You can read more about all these subjects in my signature link right at the bottom of this post. Good luck with it and happy installing! (Herman)

---

