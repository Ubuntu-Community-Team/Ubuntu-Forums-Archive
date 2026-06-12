---
title: "Restoring GRUB via Live CD"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-05-26
I want to install GRUB again due to repeated problems but when i run the live cd, after typing "sudo  grub", i type "find /boot/grub/stage1" and the system says that cant find the file. I rebooted my machine, entered Ubuntu, went to /boot/grub and the file stage1 was there. Can someone tell me whats going on here?

---

### Post by taurus on 2007-05-26
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by smoker on 2007-05-26
there's a couple of ways to reinstall grub at this link:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

best of luck

---

### Post by louieb on 2007-05-26
Do you have a separate boot partition? If so then use **find /grub/stage1 **
Don't ask me why but thats the way it works.

---

### Post by ferpadro on 2007-05-26
wow, that did the trick thanks. One more thing: if i create manually the partition which will run on /boot, which of the filesystem types do i have to assign to it? ext2, ext3 or other? i installed ubuntu on an ext2 partition, but i dont know very well the difference

---

### Post by louieb on 2007-05-26
ext3 is ext2 with journaling. what that means is your data is safer on an ext3 partition. But at the price of some disk space overhead. I normally don't use a separate boot partition but when I do it's  formatted ext2. Everything else is formatted ext3 (except swap of course).

---

