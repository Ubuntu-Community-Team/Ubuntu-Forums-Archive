---
title: "Problems with Bootloaders =("
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by sosamv on 2006-10-05
hi! I just installed Ubuntu linux on my 2nd hard drive and Grub was installed on MBR of the 1st one (master) and it was fine but under Grub's menu Windows Xp wasnt showing, so i decided to install GAG... when the menu appears i can choose between win and ubuntu, Windows Xp works fine, but ubuntu wont load from GAG and im only getting a black screen with a lot of 9's 

Could it be a problem with GAG? or Ubuntu can only start using Grub or lilo??

I removed GAG as well and restored my MBR, how can I get into ubuntu again? =..(

Hope you can help me guys
Ciao!

---

### Post by divague on 2006-10-05
use this guide to restore grub

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by Kateikyoushi on 2006-10-05
Try to reinstall grub by following this guide
[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by bulldog on 2006-10-05
Of try this one,

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.
The MBR of the hdd where Ubuntu is on for your info.
You can easely add the windows boot but have to change the boot order of your hdd's.
Or keep them separated,your choice.

---

### Post by anaconda on 2006-10-05
I understand that ubuntu can only be be started using lilo or grub, but if you want to use some other bootloader it is possible to install grub to the beginning of your ubuntu-partition.. and have the other bootloader (in mbr) to boot to grub, when you want to boot to ubuntu.

Quite the same way than in windows.. Grub just gives command (chainloads) to windows boot manager when you want to boot to windows.

---

### Post by sosamv on 2006-10-05
Thanx!

---

### Post by sosamv on 2006-10-05
i thought so... yeap i will reintall grub on my 2nd HD and GAG on MBR of the 1st one =)

---

### Post by confused57 on 2006-10-05
> **sosamv said:**
> i thought so... yeap i will reintall grub on my 2nd HD and GAG on MBR of the 1st one =)

That sounds like a good, workable plan.
If you don't mind opening up your computer & switching drives, you could check out this option:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

