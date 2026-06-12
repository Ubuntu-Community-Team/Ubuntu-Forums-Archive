---
title: "how do I log in as root?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by BuckoA51 on 2007-04-21
I finally got my Ubuntu to boot, through BootitNG. I had to install Grub to the boot sector rather than the MBR, even though Bootit was not on the MBR of that drive, it still would not boot Ubuntu unless I put GRUB on the boot sector instead. (my head hurts :( )

Anyway, I need to edit a file on my computer, the file is "menu.lst" it is a file to do with the GRUB boot loader, basically I need to change 1 number in this file so that my computer will boot Ubuntu (yes finally) If I can't change it I have to manually edit the boot menu (by pressing E when GRUB is loading up) every time I try and boot Ubuntu (better than having to change my BIOS I guess)

However, when I am logged on as my regular account, I do not have permissions to edit this file. I tried to log in as root, but I get an error that says "the administrator cannot log in from this screen"

I know working as root is something to be avoided (look at the problems Windows has) but how else can I change this file?

---

### Post by MrHorus on 2007-04-21
> **BuckoA51 said:**
> 
However, when I am logged on as my regular account, I do not have permissions to edit this file. I tried to log in as root, but I get an error that says "the administrator cannot log in from this screen"

I know working as root is something to be avoided (look at the problems Windows has) but how else can I change this file?

Ubuntu uses sudo, an alternative to root so that you don't accidently damage anything.

If you want to do a privilaged operation then prefix the command with sudo and you will be prompted to enter your password - then you can carry out the command.

If you want to actually get a root *prompt* then just type sudo -i (for interactive), fire in your password and that's you.

However,  if like me you find sudo incredably annoying and patronising (*grin*) then running sudo su will enable you to enter a proper root password but make sure you know EXACTLY what you are doing when you do this - it will enable a real root account and will mean that if you are running sshd then people can login as root or escalate to root with a compromised account.

YMMV

---

### Post by sad_iq on 2007-04-21
Put **sudo** in front of the comand you want to use...it will prompt for your password...and will let you run that command as root user

---

### Post by Boreras on 2007-04-21
you can become a superuser in a terminal by adding "sudo" (or "gksudo") before the command. So in order to change the particular menu.lst do something like "sudo nano /boot/grub/menu.lst" or pico or your favorite editor.
Good luck.

---

### Post by Taigrr on 2007-04-21
I think you can just use "root" inplace of your username. But don't take my word for it!

However, in a terminal, if you type "sudo gedit <path to your menu.ls file>", it'll open in Gedit, and will allow you to change, and save changes. =D


Example of <path to your menu.ls file>, would be "/etc/apt/sources.list". I just don't remember where the menu.ls file is off the top of my head... 	](*,)

---

### Post by Patrick K on 2007-04-21
Menu.lst is at /boot/grub/menu.lst.

---

### Post by BuckoA51 on 2007-04-21
Thanks, with a bit of experimentation I got this to work but I wondered, can I use sudo without going to the command prompt, e.g. if I click an icon in windows I can right click and select "run as administrator" is there a way to click and select "run as sudo" in Ubuntu/Linux?

Thanks for your help.

---

### Post by bodhi.zazen on 2007-04-21
> **BuckoA51 said:**
> I finally got my Ubuntu to boot, through BootitNG. I had to install Grub to the boot sector rather than the MBR, even though Bootit was not on the MBR of that drive, it still would not boot Ubuntu unless I put GRUB on the boot sector instead. (my head hurts :( )

Anyway, I need to edit a file on my computer, the file is "menu.lst" it is a file to do with the GRUB boot loader, basically I need to change 1 number in this file so that my computer will boot Ubuntu (yes finally) If I can't change it I have to manually edit the boot menu (by pressing E when GRUB is loading up) every time I try and boot Ubuntu (better than having to change my BIOS I guess)

However, when I am logged on as my regular account, I do not have permissions to edit this file. I tried to log in as root, but I get an error that says "the administrator cannot log in from this screen"

I know working as root is something to be avoided (look at the problems Windows has) but how else can I change this file?

the above advice by MrHorus is best : ```
sudo -i
```

If you must be root, you need to set a root password first.

```
sudo passwd
```

Set your password, log out, log in as root.

---

### Post by orb9220 on 2007-04-21
> However, in a terminal, if you type "sudo gedit <path to your menu.ls file>", it'll open in Gedit, and will allow you to change,

actually that is gksudo gedit for gui based programs.

---

### Post by aysiu on 2007-04-21
Read this if you don't want to make all your *sudo* changes in the terminal:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Sef on 2007-04-21
> Read this if you don't want to make all your sudo changes in the terminal:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Thank you aysiu.  You resolved a problem for me with that post. :)

---

### Post by BuckoA51 on 2007-04-21
Thank you that explains it perfectly. I can now dual boot (should that be tri-boot) Vista, XP and Ubuntu with one click!

---

