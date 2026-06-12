---
title: "GrubEd with Vista??"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-04-19
Has anyone used GrubEd to sort out dual-boot problems with Vista?
I've used it with great success with edgy and XP and was just wondering..

---

### Post by Tomosaur on 2007-04-21
> **Milt888 said:**
> Has anyone used GrubEd to sort out dual-boot problems with Vista?
I've used it with great success with edgy and XP and was just wondering..

GrubEd itself cannot fix any problems you may be having with your dual-boot setup. It is only really supposed to make customising Grub a bit easier. However, GrubEd should work just fine once your dual-boot setup is working correctly. You'll need to provide more information though, before anybody can diagnose your problem. Do you get errors upon booting, or does one of your operating systems simply refuse to boot? Try to give as much information as possible, I'm sure someone can help you.

---

### Post by Milt888 on 2007-04-21
I have Vista installed and have downloaded Feisty but haven't installed it yet.
I'm going to do that and probably will need to redo grub in order to get Vista back.
I just wondered whether GrubEd would allow Vista to be booted without reconfiguring grub; I guess not.
Anyway, it's a good prog.
Thanks

---

### Post by Tomosaur on 2007-04-21
> **Milt888 said:**
> I have Vista installed and have downloaded Feisty but haven't installed it yet.
I'm going to do that and probably will need to redo grub in order to get Vista back.
I just wondered whether GrubEd would allow Vista to be booted without reconfiguring grub; I guess not.
Anyway, it's a good prog.
Thanks

If you install Vista first, then Feisty, you should have no problems. Grub (not GrubEd!), should automatically detect that Vista is installed and configure itself automatically. If it doesn't, try running 'sudo update-grub' via the command line to force Grub to rescan for operating systems. GrubEd as it is does nothing to detect operating systems etc. It is only a GUI to configure an existing grub installation: changing the default boot, adding a boot splash, etc etc. It is grub which should allow vista to be booted. Provided you don't do something silly, you shouldn't need to mess with a clean grub installation, vista should continue to boot fine.

---

### Post by Milt888 on 2007-04-21
O.K. Thanks

---

### Post by freebird54 on 2007-04-21
To avoid potential problems - PARTITION/RESIZE operations on Vista should be done with Vista - BEFORE beginning install procedures.  Apparently Vista hsa change the 'definition' of NTFS enough to make the LInux partition tool incapabel of correct operation.  

Just a thought - before you do it :)

---

### Post by Milt888 on 2007-04-21
I had seen that discussed earlier.
Thanks for the heads up though.

---

### Post by freebird54 on 2007-04-21
Just trying to keep the 'Where did Vista fo?' threads to a minimum! :D

---

