---
title: "Changing Boot Order"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by the_dave on 2006-09-26
OK, I'm very new so be gentle..

I want to change the boot order in grub so that the system will automatically boot to Windows if left unatended. I have tried using the loaded documentation which instructs me to open an application in System Tools which is not there. I can open the "menu.lst" file but don't know enough about syntax to be comfortable making any edits at this stage. 

I know someone out there can help...

---

### Post by Bachstelze on 2006-09-26
Just paste the contents of the file here, someone will tell you what you need to do :)

---

### Post by dbd on 2006-09-26
There is probably another way of doing this, but editing menu.1st is pretty straightforward.

Near the top of menu.1st there will be a line which is probably:
default 0
This means that the default OS to boot is the first one in the list (computers like to count beginning with 0). So just count which number in the list of windows is, and then change the default number to that -1. (Because it counts starting with 0, if windows is 3rd in the list you want default to be 2). 

An alternative solution is to move the windows section of menu.1st to the top of the bootloaders, so that it is first in the list, so if default is 0 then it will select windows.

By the way, to edit menu.1st you need root permissions, so on the command line window go to the menu.1st directory and open it with the sudo command, followed by the name of your text editor, followed by the file name, so to open with kdedit I would use:
sudo kedit menu.1st

Good luck :)

---

### Post by xyz on 2006-09-26
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
sudo gedit /boot/grub/menu.lst
```

Then you locate the line you just opened (default 0)

Replace "0" with the option you want. You must start counting from "0".
Good luck.

---

### Post by the_dave on 2006-09-26
Thanks. I tried dbd's answer and that worked fine. Being an established Windows user I have so much to learn so thanks again for the help with this. I am now on my way........

---

