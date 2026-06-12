---
title: "lockup at login after update and package removal"
date: 2006-10-20
forum: Apple PPC Users
---

### Post by hanjet on 2006-10-20
Hi,
I recently installed Ubuntu on my macbook following a guide (not sure which one, but I found it on the forums here and its in PDF format..). Everything worked fine until I got to a part where it said to remove the smp 386 kernel packages and the kernel itself. I did this, and then installed updates. When I restarted, at the login, I couldn't move my mouse or press any keys on my keyboard...
I tried restarting but it doesn't change a thing.

Please help

thanks

edit: i used hank koster's guide found here: [http://www.xs4all.nl/~hajk/](http://www.xs4all.nl/~hajk/)

---

### Post by taurus on 2006-10-20
I am going to move this over to the Mac section...

---

### Post by hanjet on 2006-10-20
ok. I tried reinstalling again, and narrowed down the problem to the package removal. Is there any way I can remove the packages without getting this stupid lockup after I restart? Am I getting the lockup because I'm deleting the wrong package?


thanks

---

### Post by taurus on 2006-10-21
What packages did you remove and how did you remove them?  If you install the i686 kernel, then you can remove the default, i386, but you can't remove both since you need at least one to boot the machine.  I suggest you install the i686, boot from it to make sure it work, then remove the i386 using synaptic!!!

---

### Post by hanjet on 2006-10-21
Oh... I did what the guide said, which is to search "386" in the name field, and delete all packages that are installed. There were about 5-6 packages. Before I did this, I rebooted to see if it worked. How can I tell if I rebooted in 386 or 686? 

Edit: I'm planning to reinstall a third time now. What are the steps I should take to make sure the 686 kernel is working and booted, and which packages should I delete?

Thanks

---

### Post by mlissner on 2007-02-10
When you're booting, if you have two kernels installed, it will give you the chance to choose one in the grub menu. You'll have to hit escape to show the menu, then once you have, you can choose a kernel if you have more than one installed.

---

