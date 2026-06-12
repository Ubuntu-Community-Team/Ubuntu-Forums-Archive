---
title: "error 15 file not found"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by dineshs on 2008-03-06
I am new to linux and is using Ubuntu 7.10. I installed Fedora and now I dont find Ubuntu in the boot list.I can see the contents .How can I restore ubuntu by editing grub.Kindly help

---

### Post by RealPSL on 2008-03-08
Did you install fedora to separate partitions than you installed fedora? If not then it is probably not recoverable. If you did which partition did you install Ubuntu on and can you provide your grub.conf file.

---

### Post by angry_johnnie on 2008-03-09
So you can boot into Fedora?  Can you see your Ubuntu partition once you're in your new system?  Try going to your Ubuntu partition and find /boot/grub/menu.lst.   Copy the entries you find there and paste them onto Fedora's GRUB list.

---

