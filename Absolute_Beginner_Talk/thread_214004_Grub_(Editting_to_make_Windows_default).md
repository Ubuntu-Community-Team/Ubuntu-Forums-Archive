---
title: "Grub (Editting to make Windows default)"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by squirrel machine on 2006-07-12
Im 2 days into to using ubuntu, and along with it i usually use windows xp, for conveniences i'd like XP to load up by default by the GRUB loader.

I tried editting the file boot/grub/menu.lst , to do so, but it turns out i didnt have the rights to edit it.. so another problem, i dont think im the admin, yet im the only user, and i didnt set up any other accounts.

How can i check that i am admin, or set my current user to have full rights, and how can i go about making XP be my default OS. Any help would be appreciated.

---

### Post by Phosphoric on 2006-07-12
I think to you need to put sudo in front of the command which gives you temporary admin rights.

ie:  sudo gedit boot/grub/menu.lst

it will then ask you for your password and let you in!

Try that.

---

### Post by user1397 on 2006-07-12
okay, in ubuntu, the root (admin) account is disabled by default.  Instead it uses **sudo**.  For more info, read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For your case, i would first type in a terminal (applications > accessories > terminal): ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` to back up your current menu.lst file.  Then you can edit the file using gedit: ```
gksudo gedit /boot/grub/menu.lst
``` you would scroll down to the bottom where your grub entries are, and you would put your windows entry as the first entry of the list.  then save and close, and it should work.

---

### Post by Ragazzo on 2006-07-12
You should move the Windows entry before line "### BEGIN AUTOMAGIC KERNELS LIST
", otherwise it may disappear when a new kernel is installed.

---

### Post by mcduck on 2006-07-12
..or leave the windows entry where it is, and change the line 'default=0' so that if the windows is 5th entry in your list, the default number is 4 (grub entries start from 0).

Or change the line to 'default=saved' to make grub default to last used entry.

Don't put anything between the lines about 'automagick kernel list'.

---

### Post by Sonic Alpha on 2006-07-12
You may find [this]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst") of use. [The whole page]("http://users.bigpond.net.au/hermanzone/p15.htm") shows you how to select windows as the default OS, change the timer, and even hide GRUB if you want to (plus a lot of other things).

---

### Post by squirrel machine on 2006-07-13
Thanks, i got it set up nicely now 

Ahh.. now i see why root is locked off :)

---

