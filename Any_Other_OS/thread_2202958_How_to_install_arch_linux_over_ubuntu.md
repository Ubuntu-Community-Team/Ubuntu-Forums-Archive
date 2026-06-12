---
title: "How to install arch linux over ubuntu???"
date: 2014-02-01
forum: Any Other OS
---

### Post by abellesle on 2014-02-01
Hi friends,
           i have an old p4 2.66ghz with 1.5 gb ram and a 1TB HDD and A nvidia Gt520.
There are almost 6 os'es installed in that system. i am using win 8 bootloader which currently loads linux via the neogrub or something like that.... Now  my question is How to install arch linux over the Ubuntu 12.04 install without changing my boot loader to grub which dosent load my windows 8. any suggestions???
Currently it has a win7, 2 win xp, win 8 and ubuntu...
i want to install arch linux because its fast...
reply soon....

---

### Post by Bucky Ball on 2014-02-01
*Thread moved to  **Other OS/Distro Support.***

Try a minimal install of Ubuntu. That's fast, too. Arch will *probably* be the same speed once you install all the packages you have in a regular default Ubuntu install. If that's what you intend to do.

If you're not using grub anyway, not sure I understand the question. Simply delete the Ubuntu partition and install Arch there. Install the Arch grub to the same partition you're using for Arch and NOT sda.

---

### Post by sammiev on 2014-02-01
[Here's]("http://news.softpedia.com/news/A-Beginners-Guide-to-Installing-Arch-Linux-352365.shtml") a good how to.

---

### Post by abellesle on 2014-02-01
Thank you for your replies but i intend to keep win 8 bootloader as default after installing jolios or arch over ubuntu...
pretty tired of ubuntu

---

### Post by Bucky Ball on 2014-02-01
> **abellesle said:**
> Thank you for your replies but i intend to keep win 8 bootloader as default after installing jolios or arch over ubuntu...
pretty tired of ubuntu

In that case, why are you asking questions here? Simply uninstall, wipe the Ubuntu drive, it's really easy (and two second of research would have proved the fact) and move on. I advise you to start asking questions on the Arch forums. That's why they're there:

[https://bbs.archlinux.org/](https://bbs.archlinux.org/)

It's about that easy ...

All the best. ;)

---

### Post by mips on 2014-02-02
Simple, format the partitions you use for Ubuntu, install Arch to those partitions, **do not install grub**, edit the neogrub config file to point to the Arch install. [https://wiki.archlinux.org/index.php/NeoGRUB](https://wiki.archlinux.org/index.php/NeoGRUB)

At the expense of sounding condescending if you are asking about something as relatively 'simple' as this you might end up struggling with the Arch install. Arch use to have a nice simple ncurses installer but they dropped this and some people even battled with that, now the install process is much more complicated and way longer as you have to do everything manually, chrooting into the install etc with no installer prompting you each step of the way. Read the [beginners guide]("https://wiki.archlinux.org/index.php/Beginners%27_Guide") and [installation guide]("https://wiki.archlinux.org/index.php/Installation_Guide"), see if you are comfortable with all this.

I'm not saying you're not capable of doing this I just wanna warn you about what you are in for.

If you wanna try arch with less intervention try Archbang as I think they still use the ncurses installer and it comes with Openbox bare bones system. Another option is a derivative or Arch call Manjaro, they have a net install image which still uses a ncurses installer very similar to the old Arch one (slighly modified I think) which will get you a minimal system without a desktop or window manager, they also have other full versions available.

---

### Post by abellesle on 2014-02-03
Thanks guys but i need to know how to install any linux os without grub.. i know how to edit the neogrub file using windows..i;ve done it before
Thank You for ur fast replies

---

### Post by Dave_L on 2014-02-03
Does this help?

[https://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot#Using_Windows_boot_loader](https://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot#Using_Windows_boot_loader)

---

### Post by lykwydchykyn on 2014-02-03
> **abellesle said:**
> Thanks guys but i need to know how to install any linux os without grub.. i know how to edit the neogrub file using windows..i;ve done it before
Thank You for ur fast replies

Well with Arch it's easy:  don't install grub.  It doesn't install any bootloader unless you explicitly do so.

For most other distros, there's typically a point in the install in which you're prompted to install a bootloader, and can opt not to.

---

