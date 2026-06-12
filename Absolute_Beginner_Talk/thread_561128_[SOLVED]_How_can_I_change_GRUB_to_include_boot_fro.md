---
title: "[SOLVED] How can I change GRUB to include boot from my partioned drive (dual boot)"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-27
Hi, I hope I put the title out right, well I have a functional XP on my drive partition I use for gaming and Photoshop, was wondering how I can boot into it, at the moment GRUB is only giving me Feisty option, can I manually go and change the grub file to include XP as a dual boot option, if so please how do I do that, thanks.

(this all happened because I partitioned my ubuntu home and then installed windows later to it, thus I lost grub totally and had only the windows boot option, then I fixed GRUB so I could boot into ubuntu again, that works fine, now I only wish to include the dual boot option into it as it's only giving me the ubuntu boot option, is that possible, is there a simple fix to the problem?)

---

### Post by overdrank on 2007-09-27
> **MozartlovesUbun2 said:**
> Hi, I hope I put the title out right, well I have a functional XP on my drive partition I use for gaming and Photoshop, was wondering how I can boot into it, at the moment GRUB is only giving me Feisty option, can I manually go and change the grub file to include XP as a dual boot option, if so please how do I do that, thanks.

(this all happened because I partitioned my ubuntu home and then installed windows later to it, thus I lost grub totally and had only the windows boot option, then I fixed GRUB so I could boot into ubuntu again, that works fine, now I only wish to include the dual boot option into it as it's only giving me the ubuntu boot option, is that possible, is there a simple fix to the problem?)

Hi this may help
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Good luck!

---

### Post by 5-HT on 2007-09-27
You'll need to add an option to boot XP in your menu.lst.
An example for windows is shown nearish the bottom of the this page from the official grub manual: [http://www.gnu.org/software/grub/manual/html_node/Configuration.html#Configuration](http://www.gnu.org/software/grub/manual/html_node/Configuration.html#Configuration)
Use that as a template, editing for the appropriate filesystem, and you'll be good to go.
cheers,

---

### Post by MozartlovesUbun2 on 2007-09-27
> **5-HT said:**
> You'll need to add an option to boot XP in your menu.lst.
An example for windows is shown nearish the bottom of the this page from the official grub manual: [http://www.gnu.org/software/grub/manual/html_node/Configuration.html#Configuration](http://www.gnu.org/software/grub/manual/html_node/Configuration.html#Configuration)
Use that as a template, editing for the appropriate filesystem, and you'll be good to go.
cheers,

Thanks, I'm looking into it right now, cheers.

---

