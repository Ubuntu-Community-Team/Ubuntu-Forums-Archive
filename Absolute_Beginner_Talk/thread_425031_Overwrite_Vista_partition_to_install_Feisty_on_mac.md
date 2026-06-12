---
title: "Overwrite Vista partition to install Feisty on machine with XP/Vista"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-04-27
I have dual booting system Partition#1: XP- Partition#2: Data (FAT32)-Partition #3: Vista; I installed Vista after I had Xp on first, so Vista's boot menu allows me to boot into Xp or Vista. I wish to format the Vista partition and install Feisty on there (ext3, plus swap). Will Feisty be able to recognize the XP install and update my boot menu using its GRUB??

Appreciate a reply before I put myself into hot waters,

Thanks

---

### Post by alienexplorers on 2007-04-27
I am running dual boot with XP and Ubuntu and have had no problems.  Ubuntu's grub boot loader recognizes XP with no problems.

---

### Post by canadianwriterman on 2007-04-27
Yes, Ubuntu will recognize your remaining XP partition. It will not add it to your current bootup menu, of course, but will replace that menu with a GRUB menu, listing any OS on your system. The default boot OS after that will be Ubuntu, but you can edit GRUB to change the boot preference.

---

### Post by vanadium on 2007-04-27
I am pretty sure it will. During setup, you will designate your current Vista partition for Ubuntu, and the installation process will automatically configure  the grub menu to reflect the actual situation.

---

### Post by shuttleworthwannabe on 2007-04-27
Thanks much appreciated

---

