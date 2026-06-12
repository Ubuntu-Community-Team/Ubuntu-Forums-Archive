---
title: "Stuck in grub, ERASE everything?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-01-08
ANYBODY OUT THERE????

I have been looking for an answer for a while but no luck so far. Should I erase everything and make a new install? 

ubuntu does not start after seeing the grub menu. It gives error at the start up, i CANNOT GET INTO THE login screen, I can see ubuntu/ubuntu safe mode start up:

init:rcS process ( 1988 ) terminate with status 2
init: rc2 ( 1994 ) process terminate with status 2.

Would you please show how I can recover? I run "safe mode" and get into su. But after that what do I do? Would you please inform step by step, or direct me to stg detailed link, I am new to linux.

Thanks in advance,
findik

---

### Post by scrooge_74 on 2007-01-08
Post more details on what kernel are you using and your config, maybe someone could be able to help you.


Can you log in after using the recovery mode?

---

### Post by findik1 on 2007-01-08
thanks for the reply

yes I can get into recovery mode.

I dont know what you mean with which kernel/config? Basically I was regular user and wanted to uninstall some software (vmware workstation) for a clean setup. It looks like I dont have anymore rc2, rc3..  directories under /etc

Partitions can be seen by Gparted with correct sizes...

---

### Post by scrooge_74 on 2007-01-08
Those directories you seem to have missing are the ones that shoud start things when you boot.

I really can give you any more pointers if you have your /home folder in another partition I would go with a clean install of the system

---

