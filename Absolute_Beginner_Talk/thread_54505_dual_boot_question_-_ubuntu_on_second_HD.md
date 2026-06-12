---
title: "dual boot question - ubuntu on second HD"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by anvil on 2005-08-04
I have installed ubuntu onto a second hard drive while windows XP is on the first. When I boot, it goes straight into windows without recognizing the second operating system unless I change the HD priority in the BIOS to boot from the second drive. When I do this, GRUB recognizes that there is another operating system (namely windows XP), but when I choose XP it does not load, instead going to a prompt, at which point I am lost, being new to linux.

Is there a way to use either boot loader to make choosing easier?

I welcome any sugestions...


Oh, one more quick question: When I installed ubuntu, i did not create a root user, did it do that for me? I have no problem reinstalling but I do not recall being prompted to create a root user. Thanks.

---

### Post by grofaz on 2005-08-04
I'm new to linux myself, and have set up ubuntu on a second hard drive also. I did everything default and installed the grub boot loader onto my master hard drive (hda, the one with Win XP). When I boot up the default is ubuntu but I can scroll down the grub menu and select Win XP if I want to boot up windows. Works pretty well for me. Might try reinstalling using default choices.

---

### Post by Omnios on 2005-08-04
You can get grub from Synaptic in Ubuntu but have no idea if you have to set it up.

---

### Post by sooqing on 2005-08-05
[QUOTE=anvil]When I installed ubuntu, i did not create a root user, did it do that for me? I have no problem reinstalling but I do not recall being prompted to create a root user. Thanks.[/QUOTE]

ya.. i was shocked too when i first installed ubuntu.. no need to login as root, just sudo all..

---

### Post by xmastree on 2005-08-05
[QUOTE=anvil]Is there a way to use either boot loader to make choosing easier?[/QUOTE]Depends on your BIOS. I have an Asus A7V8X-X and when the logo comes up, I can press 'tab' followed by 'esc' and I get a menu listing all physical drives. I just select primary slave for ubuntu.

There is a way to install the boot loader on the primary master (Windows) disk, which would be the easiest option. Try [**this**](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

