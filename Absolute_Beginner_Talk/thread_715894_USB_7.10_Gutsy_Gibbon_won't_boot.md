---
title: "USB 7.10 Gutsy Gibbon won't boot"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Spiggy on 2008-03-05
I installed 7.10 Gutsy Gibbon on a 4 GB USB drive, changed the boot sequence on my computer and I thought it was going to work but it just doesn't boot. 

So I used the **sudo apt-get install lilo** command and l**ilo -M /dev/sdb** but I get the following message: 

Fatal: creat /boot/boot.0810: Permission denied

Now what? :( Thanks in advance. =)

---

### Post by saj0577 on 2008-03-05
You tried on a different computer?

Saj

---

### Post by Spiggy on 2008-03-05
> **saj0577 said:**
> You tried on a different computer?

Saj

No, I didn't, I only have one computer. When I click on the USB disk icon it looks as if I only had two files (taking up 48,0 KB of disk space), isolinux and syslinux.cfg. 

Should I format the USB disk and try again?

---

### Post by saj0577 on 2008-03-05
Yeah i would try again it does not look as if it has worked.

First try with damn small linux as this is made for this type of thing and then try with ubuntu, once you know exactly what your doing.

Saj

---

