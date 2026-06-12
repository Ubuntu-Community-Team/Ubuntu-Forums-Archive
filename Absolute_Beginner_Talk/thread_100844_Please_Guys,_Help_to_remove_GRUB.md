---
title: "Please Guys, Help to remove GRUB"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by Hawkz Skylord on 2005-12-08
Hello Guys. Sorry for This sucker question, but I have a big problem :p ...

Look, I'm installing Ubuntu OS, wile the messege about a GRUB. I have the windows 2000 Pro installed, I click on Yes...

Because the Ubunto don't installing my mouse, I try to unistalling it, but this "GRUB" do not be removed! My friends talk about one command you need write on Win 2000 recovery Console to remove it, but nobody know...
Please Help me Guys...

---

### Post by Chayak on 2005-12-08
Boot into the windows recovery console and type ```
fdisk /mbr
``` that should fix it with 2k.  It may also be ```
fixmbr
``` but one of the two should fix the problem.

EDIT: added the fixmbr

---

### Post by Hawkz Skylord on 2005-12-08
thanks to you man!
cya !

---

