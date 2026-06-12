---
title: "Reinstall advice....?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by civicsi99 on 2007-10-19
hi everyone, its time to reinstall windows on my machine and i need some advice. im currently dual booting Feisty and XP and i want to wipe everything clean and install Gutsy, Vista, and XP. is there a particular order i should install these and how should i format the drives so that i can access and write to windows files from ubuntu? its been a while since i installed Feisty so i may be a little rusty on the process. i know in the past i had issues with booting from the live cd and my display acting all funky. im running the following:

AMD 64 X2 4600+
2 GB RAM
EVGA 7800 GT (will be installing the 8800 soon)
250 GB WD IDE
320 GB WD SATA

so i guess my question is how do i get the nvidia drivers working when i boot or install Gutsy for the first time? thanks for your help.

---

### Post by Pumalite on 2007-10-19
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by civicsi99 on 2007-10-19
i know how to setup to dual boot.......i will actually be triple booting and want to know in what order should i install vista, xp, and ubuntu. thanks. and i guess my other question is how will i be able to install the nvidia drivers if my display is all messed up? thanks.

---

### Post by Pumalite on 2007-10-19
I wouldo go: Vista-XP-Ubuntu
If blank screen at the end of install:
Ctrl+Alt+F1
sudo dpkg-reconfigure xserver-xorg
Later, install appropriate drivers

---

### Post by zero244 on 2007-10-19
Will XP recognize Vista.......dont most people install XP then Vista then Ubuntu.
Correct me if I am wrong.

Good luck

---

### Post by rsambuca on 2007-10-19
> **civicsi99 said:**
> i know how to setup to dual boot.......i will actually be triple booting and want to know in what order should i install vista, xp, and ubuntu. thanks. and i guess my other question is how will i be able to install the nvidia drivers if my display is all messed up? thanks.

I hate to contradict Pumalite, but I strongly recommend installing XP, then Vista, then Ubuntu.  Set up your partitions beforehand, so you don't have to do any shrinking/repartitioning after you have already set things up.  Install XP, then when you install Vista, it's bootloader will detect XP, and then when you install Ubuntu, grub should detect the Vista loader.

---

### Post by Calash on 2007-10-19
I think if it should be XP-Vista-Ubuntu

Vista will add XP to it's boot loader menu automatically.  Ubuntu will give you the Windows menu option that drops you to the new window.

---

### Post by civicsi99 on 2007-10-19
awesome, thanks for your  help everyone! ill post after all is done (hopefully).

---

