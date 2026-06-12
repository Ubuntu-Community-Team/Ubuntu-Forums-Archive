---
title: "Buffer I/0 error on device fd0, logical block 0"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by ilushkin on 2007-05-05
Hello! I recently reinstalled Windows and now the grub isnt loading but windows loads instead. I'm trying to run Ubuntu live cd in order to fix the grub and Ubuntu live cd won't load. I run live cd with the boot:live pci =noacpi however I get these errors all the time and Ubuntu won't load :Buffer I/0 error on device fd0, logical block 0
Please help

---

### Post by ilushkin on 2007-05-05
finally i get into some Built-in shell (ash) where it says 
/bin/sh can't access tty; job control turned off 
(initramfs)

From this point i dont know what to do next and how to fix the grub in order to dual boot windows and ubuntu....

---

### Post by ilushkin on 2007-05-05
I realized that this was my mistake. Since I build this pc myself - I had 2 cdroms and apparantly I didnt connect them right. In other words it was simply poor hardware configuration. Once I disconnected one CDROm, Live CD started!

---

