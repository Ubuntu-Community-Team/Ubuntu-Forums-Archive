---
title: "Run my Windows besides Ubuntu"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by Rongon on 2005-08-23
There is something i dont get cause i am new with Linux.
Before, i had Windows XP installed on my system (hard-disk 80GB, which has been formatted in 3 partitions; C: (16gb, this is where windows was installed), D: (32gb) , and E: (32gb). 
My friend gave me Ubuntu CDs (both Live and Install). I runned LiveCD and i fell inlove with Ubuntu, so i decided to install it. In setup (partition disk step), i choose that second partition (d:) to be Root ( / ), and for first (c:) and third (e:) i choosed "use as fat32", and setup formated only D: (like i was planning cause i had some important files on E:).
And finally, Ubuntu has finished installation and i started it. I can access the files on c: and e: , but how can i start my windows XP (which hasn't been deleted) and use 2 OS on one computer (like i used with windows 98 and windows xp) ?

---

### Post by Muhammad on 2005-08-23
Which Boot Loading program are you using? Lilo or GRUB?

---

### Post by Rongon on 2005-08-23
I am using Grub

---

### Post by davmac on 2005-08-24
[QUOTE=Rongon]I am using Grub[/QUOTE]
 If I understand you correctly, you've installed Ubuntu on what was your D: drive and now when rebooting, it goes straight into Ubuntu, without giving you the option of booting into WinXP, yes?

Have a look at [http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu) for instructions for adding the entry for windows into grub.

HTH,

Dave MacLeod

---

### Post by Rongon on 2005-08-25
It said to type:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup  
sudo gedit /boot/grub/menu.lst
```
, and sudo asks me for my password. When i type my password (which is "ubuntu"), it says:
```
Ubuntu is not in the sudoers. This incident will be reported.
``` 
, and when i type something like asdasdadfaf (i hit the keyboard) and it only says:```
Wrong password.
Try again.
```
I tried to change my root password (or just disabling it) with:
```
sudo passwd root
```
, but that also asks for password (?!?).
I don't know where  i was wrong, cause Ubuntu setup didn't asked for my root password (only for my user name and user password).

I even tried to change /boot/grub/menu.lst file manualy, but it is read-only. I saw that its owner is ROOT (right click > properties), and only owner can change it.
How to log in as ROOT?

---

### Post by PtS on 2005-08-26
When you use "sudo" ubuntu asks you for your user password. I'm new to linux too but I'm quite sure that I'm right. Correct me if I'm wrong. :)

---

### Post by weasel fierce on 2005-08-26
Yeah, the sudo password is the same as what you use to log in under your name

---

### Post by Joshua on 2005-08-26
[QUOTE=Rongon]There is something i dont get cause i am new with Linux.
Before, i had Windows XP installed on my system (hard-disk 80GB, which has been formatted in 3 partitions; C: (16gb, this is where windows was installed), D: (32gb) , and E: (32gb). 
My friend gave me Ubuntu CDs (both Live and Install). I runned LiveCD and i fell inlove with Ubuntu, so i decided to install it. In setup (partition disk step), i choose that second partition (d:) to be Root ( / ), and for first (c:) and third (e:) i choosed "use as fat32", and setup formated only D: (like i was planning cause i had some important files on E:).
And finally, Ubuntu has finished installation and i started it. I can access the files on c: and e: , but how can i start my windows XP (which hasn't been deleted) and use 2 OS on one computer (like i used with windows 98 and windows xp) ?[/QUOTE]
 Well, it looks like you haven't gotten an answer about the dual boot questions yet.  When the system is booting, right after all the BIOS stuff finishes, there should be a line at the bottom of the screen that says something like, "Grub loading" with a timer and instructions to hit ESC to setup or see options or something like that.  At that point hit the "Esc" key and see if there is already an entry for your Windows partition.  If not then follow the instructions for adding that option to the menu.

---

### Post by Rongon on 2005-08-27
I hit ESCAPE, and there shows GRUB LOADER but no Windows to run. I saw how to make it recognise Windows in FAQ :
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
Append the following lines at the end of file 

titleMicrosoft Windows
root(hd0,0)
savedefault
makeactive
chainloader+1
```

But i can't change that file cause i am not loged in as ROOT (file menu.lst is read-only and only ROOT, who is the owner, can chnage it). But my user pass which i am loging in is "ubuntu", and when i type "sudo ...." and it asks me for password and i type "ubuntu", it says the same thing i type in posts before 
 \\:D/  ```
Ubuntu is not in the sudoers. This incident will be reported.
```
I dont know what to do, except format harddisk and install Windows.

---

