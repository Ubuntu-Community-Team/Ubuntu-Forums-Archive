---
title: "Please help me fix this"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Grundalizer on 2007-06-30
I did a full install of Ubuntu from the live cd, i formatted my entire drive and erased windows and replaced it with Ubuntu.  I like Ubuntu but I have such a hard time installing programs and opening programs of certain extensions.  I am sure if i had the time and patience Ubuntu would be 100x more enjoyable but I do not.  I would like to be able to double click and install an application at times and not typing in a bunch of command lines i do not understand.  Anyway, I tried putting in my recovery cd, and it goes through the entire recovery process, takes about 30 min on this Toshiba Satellite laptop, and then when it finishes and i reboot.  At the startup screen it says GRUB not found, trying again, error. then it just sits there and does nothing.

The recvery disc obviously works but I am guessing somthing is different in the bios? if GRUB replaced DOS or somthing?  I am not a computer guru and I would just like to be able to go back to windows on this machine and put Ubuntu on my other machine to learn it at the pace I can handle.

THank you for anyone who has any ideas on how to fix this.

---

### Post by hyper_ch on 2007-06-30
you normally install software from the repositories....

---

### Post by Grundalizer on 2007-06-30
it is not just installing programs, i can figure that out at times, but also lack of linux support for a lot of programs i would like to use.

---

### Post by hyper_ch on 2007-06-30
What lack of programs?

---

### Post by tgalati4 on 2007-06-30
Your frustrations are common.  As you get familiar with Linux and Ubuntu, it will be come clear.

What particular application did you feel that you needed support?

---

### Post by mmmichael on 2007-06-30
Your windows recovery disk won't reinstall windows on a linux file system. If you really want to put windows back on this machine, use the Ubuntu live cd, go to System>Administration>Gparted. This will enable you to delete or resize the ext3 partition and create a new partition of type ntfs or fat32, depending on your windows version.

---

