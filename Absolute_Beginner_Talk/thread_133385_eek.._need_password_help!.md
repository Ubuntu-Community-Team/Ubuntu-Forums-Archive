---
title: "eek.. need password help!"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by raye on 2006-02-20
hopefully someone can help, 
i've got ubuntu dual booted with windows xp, and the ubuntu drive is linked to windows, ie i can see all the ubuntu files. The bf set it up then left the country, i've since forgotten the username and password to get into ubuntu. :(  is there anyway to change this through modifing the files from windows... or will i be forced to reinstall....

---

### Post by alamba on 2006-02-20
1. Boot into Ubuntu (Recovery mode). It should drop you to the bash shell ($ or # prompt). 
2. type useradd -m raye
3. passwd raye (enter a password twice)

Then boot into ubuntu normally and use that username and password.

Akshay

---

### Post by raye on 2006-02-20
sorry real newbie here,
when i boot into recovery mode it asks for a root password, and doesn't like anything i type in..  am i in the wrong spot..?

---

### Post by codejunkie on 2006-02-20
[QUOTE=raye]sorry real newbie here,
when i boot into recovery mode it asks for a root password, and doesn't like anything i type in..  am i in the wrong spot..?[/QUOTE]
no they set the root password perviously, once you set the root password in ubuntu it requires it, when you use the recovery mode, by default the root password is not set. you can use an ubuntu install cd to reset the root password insert the install cd at the cd boot prompt enter ```
rescue
```follow the instructions and when you reach the terminal enter ```
passwd root
```enter the root password twice while your there go ahead and add your new user account with ```
adduser
```enter in your new user info, when your finished do this so your new user can access system tools as root
```
adduser yournewusername admin
```then reboot by entering the command reboot remove the cd and login with your new user account.

---

### Post by george_apan on 2006-02-20
I just saw this HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=133102](http://www.ubuntuforums.org/showthread.php?t=133102)

---

### Post by codejunkie on 2006-02-20
[QUOTE=george_apan]I just saw this HOWTO:
[http://www.ubuntuforums.org/showthread.php?t=133102](http://www.ubuntuforums.org/showthread.php?t=133102)[/QUOTE]
yes but that will work only if the root password has never been set if someone has set the root password you need to either know it or chroot into the system with the ubuntu install cd or linux live cd, unless they have set the root, grub, and bios password and change the bios to only boot to the hd0 and then you can't get in unless you pull the harddrive.

---

