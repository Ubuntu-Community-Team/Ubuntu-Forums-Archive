---
title: "Question about boot order in dual boot system"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by Apprentice on 2005-11-30
I have a dual boot system ( Windows XP and Ubuntu) and would like to know if I can change the order in which the computer boots.

---

### Post by Robgould on 2005-11-30
yes you can.  You can edit the grub configuration file to select which option you want to boot as default.  You can change the default timer.  You can even change the order that they are in onr your screen.  This is not a thing to be done lightly, you can break your system.  
 
I'm at work and can not remember the exact name of the file you need to edit, but it is in /boot/grub
 
it is something like menu.lst
 
open it with gedit:
 
sudo gedit /boot/grub/menu.lst
 
Read CAREFULLY
 
You should save the file as another name, so that you can use it as a back-up.
 
Change it how you want it.  Save.  Reboot.
 
Good luck.

---

### Post by Xian on 2005-11-30
In the menu.lst file change the entry below to reflect 
the position that WinXP has in the boot order -1.

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0
```

For example, if WinXP is the 2nd entry then change to:

```
default    1
```

You want to avoid moving around the actual OS entries.
It's possible to cut/paste improperly and make the system unbootable.

---

### Post by Apprentice on 2005-11-30
OK, I finally found the menu.lst file.  Now,  how can I actually edit this file?
When I write gedit boot/grub/menu.lst it opens read-only.

---

### Post by Xian on 2005-11-30
[QUOTE=Apprentice]
When I write gedit boot/grub/menu.lst it opens read-only.[/QUOTE]
The command was given earlier in the thread:

```
$ sudo gedit /boot/grub/menu.lst
```

---

### Post by Apprentice on 2005-11-30
Thank you very much.  I was able to edit the file successfully.  thanks for the help.

---

