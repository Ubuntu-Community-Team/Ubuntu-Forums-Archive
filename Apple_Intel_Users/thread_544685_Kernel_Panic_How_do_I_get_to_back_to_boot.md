---
title: "Kernel Panic: How do I get to back to boot:?"
date: 2007-09-06
forum: Apple Intel Users
---

### Post by themacmonk on 2007-09-06
Hello everyone.  I'm a new user and recently installed Feisty on my MacBook.
In the Wiki instructions it mentioned to enter in the following to prevent a kernel panic 

lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)

At the time I couldn't remember the processor speed because I forgot to check before starting the installation but entered in the command for 2 Ghz.  I actually have the 1.83 Ghz model.

This may be a simple question but how do I go back and change it?

Ubuntu is booting up fine but I got my first kernel panic today and want to fix this straight away.

Thanks!

---

### Post by cyberdork33 on 2007-09-06
> **themacmonk said:**
> Hello everyone.  I'm a new user and recently installed Feisty on my MacBook.
In the Wiki instructions it mentioned to enter in the following to prevent a kernel panic 

lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)

At the time I couldn't remember the processor speed because I forgot to check before starting the installation but entered in the command for 2 Ghz.  I actually have the 1.83 Ghz model.

This may be a simple question but how do I go back and change it?

Ubuntu is booting up fine but I got my first kernel panic today and want to fix this straight away.

Thanks!

check the /boot/grub/menu.list file as I am pretty sure that is where it is.

---

### Post by themacmonk on 2007-09-06
I looked in the folder you suggested and don't see it in there.  It might not have originally taken so how would I add this in?  Would it be best to do a re-install? 

Thanks again!

---

### Post by cyberdork33 on 2007-09-06
> **themacmonk said:**
> I looked in the folder you suggested and don't see it in there.  It might not have originally taken so how would I add this in?  Would it be best to do a re-install? 

Thanks again!

You can just add it to the end of the kernel lines in the menu.list file. Above that, there is an option for 'default' kernel options or something like that. it will continue to add that at the end for any new kernels. If you read through the "AUTOMAGIC KERNEL OPTIONS", it kinda tries to explain how that works.

---

