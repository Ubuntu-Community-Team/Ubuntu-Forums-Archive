---
title: "Have I just hosed Ubuntu 6.06?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-14
I had Ubuntu 6.06 installed on my laptop, and I just decided to install XP so I can use Access for college work (dual boot). However I now cannot access my Ubuntu OS at startup. Have I just messed up my Ubuntu partition or can I change something so I can access it as well as XP at boot up?

Cheers

---

### Post by bollix47 on 2006-11-14
You might be able to restore grub using the method explained [here.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by marx2k on 2006-11-14
Easiest GRUB reinstall ever? Here you go:
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by cotcot on 2006-11-14
If you have installed XP on another place than ubuntu you do not have a big problem. You only overwrite the grub bootloader in the Master Boot Record with the XP bootloader. With the grub-install as mentioned in the other post it should be ok.
You can check with a live CD (sudo gparted) if you still have your ubuntu partitions.

---

### Post by gentlemanmasher on 2006-11-14
Sorry to jump in here but I have to reinstall windows tonight and will have this problem.  Do I just select option Fix boot of GNU linux or do I select Boot GNU linux.

Thanks

---

