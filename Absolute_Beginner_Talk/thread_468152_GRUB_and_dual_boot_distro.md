---
title: "GRUB and dual boot distro"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Raxza on 2007-06-08
Hi, 
I've been using Ubuntu and now I'd like to try out other Linux distro. I have some questions though, just to make sure I  won't screw up my laptop. 

Anyway, here it is: 

1. If I install another distro (say distro A), that distro will write its own bootloader on top of Ubuntu's bootloader, right? 
2. So if in the future, I decide to uninstall distro A and reformat distro A's partition, will I be able to boot into Ubuntu? 
3. I know that I should create different /home partition for each distro. Are there any other suggestions/pointers I should know before I install this other distro?

Thank you.

---

### Post by Kibe Frito on 2007-06-08
It will overwrite only if you allow it. I guess it also depends on the distro, most will ask you before. If your new distro overwrite the current grub, you can reinstall the ubuntu grub and overwrite it again. You can also manually add the new OS into the grub menu.

---

### Post by Raxza on 2007-06-08
If the new distro does overwrite Ubuntu's GRUB, how do I re-install the Ubuntu GRUB? Can you elaborate?

---

### Post by ccfjeff on 2007-06-08
> **Raxza said:**
> If the new distro does overwrite Ubuntu's GRUB, how do I re-install the Ubuntu GRUB? Can you elaborate?

Yesterday someone posted a link to [this tutorial]("http://users.bigpond.net.au/hermanzone/") for dual booting.

One of the links was to an alternative to the Grub loader that will allow booting up to 9 different operating systems:  GAG: [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by Raxza on 2007-06-08
Thank for the link, ccfjeff. 
That really answers my questions.

---

### Post by confused57 on 2007-06-08
This might help also:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

You can always reinstall Ubuntu's grub using the live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

