---
title: "urgent help required-boot upquestion"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-03-06
okay then i have 2 HDD's in my box. one runs linux-ubuntu andthe other did run XP until a few hours ago. My ubuntu was master and xp slave with ubuntu having an OS selector. My xp had a virus and i had to format it. my XP disk is broken some how so im realing on linux to work.However i cant because the OS selector cant give a choice meaning it never loads o my box  crashes.      Im on my dads laptop right now and its a good job i can ask aswell

(if this doesnt make much sense ive posted it on 3 diferent forums about diferent things so some infor may seem obvious)

---

### Post by ajgreeny on 2006-03-06
Your problem is that in reformatting the windows partition you have also got rid of the master boot record (MBR) which contained grub.  The menu.lst file in /boot/grub, which grub depends on, should still be there so you will need to reinstall grub using either the ubuntu installation disk or a live linux CD.

Look up "reinstall grub" in these forums, there is plenty of detail already here.

---

### Post by cotcot on 2006-03-06
Reinstall grub as previous post says : [http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=MBR+messed)

---

