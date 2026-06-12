---
title: "Can't install k7 kernel"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Nannygoat on 2006-05-07
Hello,

please excuse my bad english, I hope I'll manage to explain the issue clearly. I'm trying to install the linux-k7 kernel for Ubuntu 5.10 Breezy but the console returns the following error: 'e: couldn't locate the package' on 'sudo apt-get install linux-k7'. What am I doing wrong, am I missing some dependencies? Thank you for your help in advance!

---

### Post by silentb on 2006-05-07
that's odd.

look into your repository list. is "restricted" listed there (it is by default)?

---

### Post by AnRuaRi on 2006-05-07
I would reccommend doing this from the Synaptic Package Manager.
(I assume you have a GUI installed, andy you're not restricted to the terminal)
when logged in as an administrator:
Click on System -> Administration -> Synaptic Package Manager

Enter your password in the dialogue box

Ensure you have the Universe and Multiverse repositories installed

Ensure your repositories are up to date (press Reload)

on the bottom Left, press "Sections"

in "Base System" section, scroll down in the list to 'Linux' "

Mark the Linux-image-2.6.12-10-k7
(or Linux-image-2.6.12-10-k7-smp if you have multi processors)

mark "Linux-image-k7"

Click "Apply"

once complete, reboot your computer,
Enter the bootloader (Grub or Lilo), 
select the k7 linux image. Check it works.

If you wish to, you can uninstall the x86 version of the kernel, but I would recomend leaving it installed for now, but configure your bootloader to load the k7 image by default untill you're hoppy it's working properly

---

