---
title: "Boot manager"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by alecsino on 2008-02-01
Hello,

I have, from the release date, Ubuntu 7.10 and XP on my PC, they are installed on different partitions (C:\ and F:\).

I had recently problems with my XP. I reinstalled XP, and after that my boot manager from UBUNTU would not load, and I can't start UBUNTU. If the boot manager does not start the default operating system loaded is XP.

Could I get the boot manager start?

I just want my UBUNTU back, can anybody help me?

Thankx a lot,
Alecsino

---

### Post by jan quark on 2008-02-01
i guess the reinstalling of XP deleted the grup loader, correct me if I am wrong

you have to manually restore grub using the super grub cd
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

see also the documentation of super grub 
[http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation)

---

### Post by alecsino on 2008-02-01
Hi,

Thanks for your quick response. I have burned 1 CD with SUPER GRUB, restarted my PC and went through all the steps for installing it and recover UBUNTU boot manager. After I did thatI restarted my pc, and the boot manager apeared. I selected Ubunt 7.10, and it says ERROR: Partition is not available!.

In the attached picture u will see my partitions and my linux partition. I do not understand why it won't start Ubuntu.

Thank you.

---

### Post by alecsino on 2008-02-01
Acctually it says "Error 22: No such partition".

Anyway thanks a lot Jan Quark!

---

### Post by jan quark on 2008-02-01
read this should help
[http://ubuntuforums.org/showthread.php?t=378322](http://ubuntuforums.org/showthread.php?t=378322)

and ask for more :)

---

### Post by alecsino on 2008-02-01
Thankx a lot.

I was pointing to ( hd0/8 ) and it was wrong of course. I changed it to ( hd0/6 ). This was correct and it worked.:)

---

### Post by jan quark on 2008-02-01
i am glad I could help you 

please mark this thread as solved so that other users will find the solution quicker
you can do this with the thread tools at the top of the page

---

