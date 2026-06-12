---
title: "2 problems! unknown reason!"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-07-03
Hi guys have 2 problems bugging me for quite some time now...please help!

1... i recently installed Beryl. After a few days of cool graphics wanted to get back to default ubuntu settings. So changed back the window manager to Metacity. But every time i boot up beryl dose not start automatically and also the windows don't have any borders...ie they are undecorated! NO close minimize resize buttons are visible. But if i start beryl..they all pop up! how do i rectify this.. will uninstalling beryl help!

2... when the system boots up i get the operating system selection menu from grup (I have dual boot ubuntu/win xp). when i select either of the oerating systems i get an error saying.. Please remove the disck and reboot. after almost a second i get the grub menu again and this time the selected os boots up!!!!! 

please dont give the solution to these probelms as reinstalling the OS.. i want that to be the last solution!...expecting some quick and permanant fixes for these as always! thanx in advance!

---

### Post by yagood on 2007-07-03
> **badguyanil said:**
> Hi guys have 2 problems bugging me for quite some time now...please help!

1... i recently installed Beryl. After a few days of cool graphics wanted to get back to default ubuntu settings. So changed back the window manager to Metacity. But every time i boot up beryl dose not start automatically and also the windows don't have any borders...ie they are undecorated! NO close minimize resize buttons are visible. But if i start beryl..they all pop up! how do i rectify this.. will uninstalling beryl help!

How did you install Beryl? Did you edit /etc/gdm/gdm.conf or add a session to /usr/share/xsessions or something else?

> **badguyanil said:**
> 2... when the system boots up i get the operating system selection menu from grup (I have dual boot ubuntu/win xp). when i select either of the oerating systems i get an error saying.. Please remove the disck and reboot. after almost a second i get the grub menu again and this time the selected os boots up!!!!! 

What is the exact error message here?

---

### Post by aquavitae on 2007-07-03
> **badguyanil said:**
> 
1... i recently installed Beryl. After a few days of cool graphics wanted to get back to default ubuntu settings. So changed back the window manager to Metacity. But every time i boot up beryl dose not start automatically and also the windows don't have any borders...ie they are undecorated! NO close minimize resize buttons are visible. But if i start beryl..they all pop up! how do i rectify this.. will uninstalling beryl help!

Yes, uninstalling beryl will help, but only do that if you don't want it anymore.  It sounds like beryl is still starting up, even if it doesn't display the beryl-manager icon.  You can check this by looking at the running process's.

> 2... when the system boots up i get the operating system selection menu from grup (I have dual boot ubuntu/win xp). when i select either of the oerating systems i get an error saying.. Please remove the disck and reboot. after almost a second i get the grub menu again and this time the selected os boots up!!!!!

Can you post the contents of /boot/grub/menu.lst.

> please dont give the solution to these probelms as reinstalling the OS.. i want that to be the last solution!...expecting some quick and permanant fixes for these as always! thanx in advance!
Don't worry, we're not microsoft:D

---

### Post by badguyanil on 2007-07-04
This is what i get when the OS boots up and shows me the OS list. I select one of the options from UBUNTU and windows XP and this is what happens...

Starting up...

Remove disks or othermedia
Press any key to restart...
GRUB loading stage 1.5

GRUB loading Please wait...
Will post GRUB menu.lst by tomo morning! any help with this input....

---

### Post by badguyanil on 2007-07-04
> **yagood said:**
> How did you install Beryl? Did you edit /etc/gdm/gdm.conf or add a session to /usr/share/xsessions or something else?

No i did not edit any thing. Just installed Beryl and Emarald theme manager!

> **yagood said:**
> What is the exact error message here?

as mentioned above!!!

---

