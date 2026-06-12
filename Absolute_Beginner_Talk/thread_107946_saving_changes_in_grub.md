---
title: "saving changes in grub"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by Icebear on 2005-12-24
I would like to change grub, so that grub on default will load up windows (at least for now till I get a better grip of ubuntu). I realize I need to change the default from 0 to 4 in the menu.lst but I am not allowed to save any changes in the boot folder and I have no idea how to use the command line

---

### Post by bscbrit on 2005-12-24
OK

open a terminal and type

sudo gedit /boot/grub/menu.lst <enter>

Do your editing, save the file. Complete.

p.s. Don't get it wrong, or you might not be able to boot at all.

---

### Post by Icebear on 2005-12-24
Thank you for the quick reply I tried what you said. Then I got asked for the pass word then i just got the same line like normal (something like icebear@icebear ~$ I have to go to windows for the net)
Then I rebooted and tried again and put the wrong password in and it asked again for the right password. so I guess it not the wrong password

---

### Post by bscbrit on 2005-12-24
You only have _one_ password.  It is the password that you use to log on, it is also the password that will let you use sudo.  If you have already logged on, you must know the password!:p

---

### Post by Icebear on 2005-12-24
Sorry for the misunderstanding I type in the password but the menu.lst did not load up. Thank you for putting up with a slow and newbie like me

---

### Post by bscbrit on 2005-12-24
No problem - have you now managed to edit the file or not?

---

### Post by Icebear on 2005-12-25
No!
nothing comes up to edit

---

### Post by Sutekh on 2005-12-25
That's totally wierd.

Are you the first user on your PC, by that I mean is your user the one you entered when you installed Ubuntu?  Also are you able to do admin kind of things, like open Synaptic?

---

### Post by Icebear on 2005-12-25
That is my problem I can not open Synaptic? some how I lost my admin rights
This might have come when I reinstalled ubuntu after making some mistakes.

Thank you

---

### Post by Sutekh on 2005-12-25
Ok, well you'll need to follow one of these methods to gain root access, then modify some settings

[Ubuntu Guide - How to gain root user access without login?]("http://www.ubuntuguide.org/#gainrootwithoutlogin")

[Ubuntu Guide - ow to use Ubuntu Installation CD, to gain root user access?]("http://www.ubuntuguide.org/#gainrootinstallcd")

[Ubuntu Guide - How to modify kernel boot-up arguments, to gain root user access?]("http://www.ubuntuguide.org/#gainrootmodifykernel")

The first link is the way to go (easiest), I linked the others in case you are not able to boot into the recovery mode.

Once in recovery mode, you need to need to add your user to the **adm** group, so you have admin privileges.
```
adduser icebar adm
```
Once you are in the **adm** group you should be able to open Synaptic, edit the menu.lst and many other important tasks

---

### Post by Icebear on 2005-12-25
w

---

### Post by Icebear on 2005-12-25
For all who helped THANK YOU :D :D 

The wife will be pleased to get the computer working to what she used to
(Don't worry I am working on getting her change to ubuntu but these things take time)

---

