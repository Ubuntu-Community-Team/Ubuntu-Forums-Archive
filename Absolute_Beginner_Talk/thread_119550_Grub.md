---
title: "Grub ??"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by acid on 2006-01-19
Hi..I was wondering..

I have Ubuntu Installed on my 2ndary HD and Win Xp on my Primary.....And i installed Grub...If i want to Remove ubuntu How do i do this ? if i reformat my 2ndary HD with Xp will Grub Mess Up my booting ? How can I safely Remove Ubuntu and Grub from my system .

---

### Post by Lunixfanboy on 2006-01-19
To remove GRUB from the mbr of the XP drive, boot from Windows XP install CD (provided you have one) and after the five or so minutes where XP reports "copying files to harddrive" it should come up with install/repair console options. Choose repair console, then from there, the commands are "fixmbr" and "fixboot", in that order.  Both commands are typed WITHOUT the quotes. After removal of GRUB, you can use Admin Tools under Storage to format the second drive.

---

