---
title: "Installing Ubuntu over SUSE in dual boot with Vista"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by SaJellish on 2008-02-06
Hello,

      I had lots of troubles installing ubuntu over my HP laptop so I finally installed SUSE in dual boot with Vista. Now hardy live CD is booting on my Laptop so I wanted to try this distro. But during installation it does not detect my Vista installation. So I refrain from installing it. In case it does not recognize my Vista then I know GRUB will only boot into UBUNTU. What is the best possible way to ensure that I do boot into Vista. Should I take a copy of my current /boot/grub/menu.lst and just add the Vista entry into the fresh installation of UBUNTU grub. I think it may work but wanted to be seconded by some pro. Also is there any better way of dual booting in this scenario ?
     Thanks.............

---

### Post by logos34 on 2008-02-06
If you're booting vista from SUSE's grub, then I'd just continue to use that, and install ubuntu grub so that it doesn't overwrite the MBR (i.e. put it on the ubuntu root partition).  Then manually [add ubuntu stanza to SUSE menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile").

When you come to the "Ready to install' screen, click 'Advanced' button lower right and replace the default '(hd0)' with the number of your ubuntu root.  E.g., if new ubuntu root is sda4, then 

> (hd0,3)

or 

> /dev/sda4

Hope that helps.

---

