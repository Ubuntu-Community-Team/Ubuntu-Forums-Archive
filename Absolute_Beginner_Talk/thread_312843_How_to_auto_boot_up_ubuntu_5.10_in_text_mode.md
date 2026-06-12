---
title: "How to auto boot up ubuntu 5.10 in text mode?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by brave.heart on 2006-12-05
In redhat linux, you can modify runlevel in /etc/inittab to change the boot up mode to text mode.

And I also changed the runlevel in /etc/inittab in ubuntu 5.10, it still can't log in text mode automaticlly.

Could anybody help me?

Thank you.

---

### Post by anaconda on 2006-12-05
I am not 100% sure BUT..

It should be enough to edit your /boot/grub/menu.lst so that your default entry boots with different runlevel..

There are also other options to boot to terminal than "single" (which is recovery mode)
try boot option 2 or 3.. if I remember correctly. 
2 might be the same than single..

EDIT: here is one link
[http://iodynamics.com/education/runlevel.html](http://iodynamics.com/education/runlevel.html)

---

### Post by brave.heart on 2006-12-05
Thanks for your fast reply.

And I will try it some late time ASAP for I will leave for a business trip for a couple of days.

Anyway, thank you so much!

:p

---

### Post by pavel_kbc on 2006-12-05
:P have fun

---

### Post by steve.horsley on 2006-12-05
All runlevels are very much the same in Ubuntu. By default, Ubuntu boots into runlevel 2. Ubutu does this because Debian does it. I don't know why Debian choose to be different to Red Hat.

The easiest way to disable gdm from starting at login is to use the command gksudo nautilus to get a full privilege file manager and then go and find the file /etc/rc2.d/S13gdm. Rename it to start instead with a lower-case s instead of S. This will prevent it from being called at startup (the upper-case S scripts are called in alphabetical order). 

To reinstate gdm, change it back to an upper-case S.

---

### Post by brave.heart on 2006-12-10
Hi, Steve

I changed the settings as you mentioned and it works.

Thanks a lot! :) 

Best regards!

---

