---
title: "getting back!"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by adam.white on 2007-05-18
ive installed ubuntu uedgy efte, and am a complete begginer. i cant really work  it verry well so want to go back to xp proffesional, but i dont know how to do it?! please help x

---

### Post by Hobo Joe on 2007-05-18
What can't you get to work?

As long as your not dual booting, all you have to do is put in the Windows CD and do a normal install.

---

### Post by hyper_ch on 2007-05-18
well, if you didn't do dual-boot, then you need to reinstall it completely.

---

### Post by Najand on 2007-05-18
Did you make a dual boot system or you just removed Windows XP?

---

### Post by theicyj on 2007-05-18
You will also want to backup any personal files and documents to a cd, dvd, or another hard drive.  When, and if you reinstall windows xp, you will lose any data on that hard drive.

---

### Post by adam.white on 2007-05-18
i dont want to dual boot, i just want to escape this grub thing and get back to windows, do i need to delete my linux partitions first or somethning??

---

### Post by mikewhatever on 2007-05-18
So, where is the Windows you want to go back to? Is it on the same PC? Is it on the same HDD?
In Ubuntu, can you open Applications>Accessories>terminal and post the output of the following > sudo fdisk -l

---

### Post by Najand on 2007-05-18
You need to go into the BIOS and set the CD to be the first device to boot, put the hard drive second.
Do you have Windows installed already? If so, boot from the CD, enter the recovery console (press R when it asks you whether you want to install windows etc.) When you're at the console, type:

fixmbr

and that will remove GRUB from your system.

If you don't have Windows installed, GRUB will be overwritten as part of the installation.

---

