---
title: "Anyone Dual Boot Ubuntu and Vista on two harddrives"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-07-05
If you do would you point me to an how to on it.

---

### Post by Raineer on 2007-07-05
Long story short, install only one HDD and install Vista on it.

Now, plug in your second HDD and install Ubuntu on that one.  As part of the Ubuntu installation it will setup a dual-boot menu that will allow you to choose between the 2 at every boot (the Linux drive should be yor boot drive).

---

### Post by Drifter on 2007-07-05
What if you already have both of them on harddrives, do u still need to install unbuntu inorder to get the boot up menu.

---

### Post by Drifter on 2007-07-05
Hello, anyone look at my last post.

---

### Post by Orochi on 2007-07-05
You can just install GRUB if Ubuntu and Vista are both already installed. In your BIOS set the Ubuntu drive as the boot drive. There are instructions here: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) on how to (re)install GRUB from an already existing Ubuntu installation. Scroll down to the section titled "Reinstall GRUB to the MBR" and keep in mind that your harddrive location and numbers will be different. Also, in their screenshot of GRUB's menu.lst they show the Windows entry being before the "END DEBIAN AUTOMAGIC KERNELS" line, when really it should be after it.

---

### Post by Drifter on 2007-07-05
Ok thanks I will give it a try.

---

### Post by Raineer on 2007-07-05
[This]("http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot") is the guide I used. Probably the same steps, you're just using the Live CD to boot and reinstall "GRUB" on the boot drive and refresh the menus.

---

### Post by Drifter on 2007-07-05
Your how to is for XP not Vista, I here that Vista has a different boot loader than XP and that it is harder to dual boot because of this.

---

### Post by Orochi on 2007-07-06
It should work exactly the same as long as you fill in the correct harddrive numbers and partitions.

---

