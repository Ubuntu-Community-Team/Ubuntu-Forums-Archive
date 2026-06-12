---
title: "Re-Grub?"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by duvel on 2005-12-10
I've been dual-booting Windows XP and Ubuntu 5.10 and last week Windows crashed and burned. Apparently it took Grub down with it because the machine would not even load it. Now, I have re-formatted the windows partition and it seems to be OK, but Grub is definitely gone:( 

How can I get Grub back on the Windows partition so that I can go back to dual booting? I would rather not re-install Ubuntu as I have done a lot of configuration/tweaking.

Thanks.

---

### Post by matthewv on 2005-12-10
You should be able to boot ubuntu to a terminal using your install cd. Then typing ```
grub-install /dev/hda
``` should reinstall grub to the mbr of your first hard drive. Hope that helps.

---

### Post by duvel on 2005-12-10
[QUOTE=matthewv]You should be able to boot ubuntu to a terminal using your install cd. Then typing ```
grub-install /dev/hda
``` should reinstall grub to the mbr of your first hard drive. Hope that helps.[/QUOTE]

Many thanks. I'll give it a try and post back the results.

---

### Post by duvel on 2005-12-10
Well, I tried using the command at the boot prompt and it did not work. I tried the help screen, but saw no way to start up the terminal at that point.

How do you start up the terminal from the boot prompt?

---

### Post by Susana on 2005-12-10
[QUOTE=duvel]Well, I tried using the command at the boot prompt and it did not work. I tried the help screen, but saw no way to start up the terminal at that point.

How do you start up the terminal from the boot prompt?[/QUOTE]

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#gainrootinstallcd](http://help.ubuntu.com/starterguide/C/faqguide-all.html#gainrootinstallcd)

---

