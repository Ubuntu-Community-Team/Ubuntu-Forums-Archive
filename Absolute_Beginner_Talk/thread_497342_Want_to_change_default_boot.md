---
title: "Want to change default boot"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by uliH on 2007-07-10
Hi everyone,

the default boot is on Ubuntu, and in order to use the old Windows XP one has to move the cursor down and use the enter=command. Since other members in the family want to use the PC in the old way, I would like to change the default boot to Windows XP. How is this done_
Thanks in advance!
Greetings from Norway
uliH

---

### Post by HereInOz on 2007-07-10
If you open a terminal and type:

sudo nano /boot/grub/menu.lst

and then enter your password, this will open up the boot list file and by reading the instructions therein, and editing it appropriately, you can change the default system.

It is not a bad idea to take a copy of menu.lst first, and save it as something else, just in case you do something evil and the boot list is lost.

Hope this helps.

---

### Post by pyros on 2007-07-10
> **uliH said:**
> Hi everyone,

the default boot is on Ubuntu, and in order to use the old Windows XP one has to move the cursor down and use the enter=command. Since other members in the family want to use the PC in the old way, I would like to change the default boot to Windows XP. How is this done_
Thanks in advance!
Greetings from Norway
uliH

you want to open up the grub menu file as root with 
```

sudo gedit /boot/grub/menu.lst

```
then you want to scroll down to the bottom and look for the windows entry.  Count the number of entries before it. on my system the windows entry is the sixth in the list.
Now scroll up until you see the line 
```

default		0

```
It should be near the top of the file. the "0" tells grub to boot the first item in the list by default. to change that, just replace the zero with the number of menu entires before the one you want to be the default. GRUB starts the numbering off at 0, so on my system, windows would be 5.

The only thing to remember is that you will have to change it every time you update the kernel.

---

### Post by pyros on 2007-07-10
if you do make a mistake, just look for the file "menu.lst~" that's an automatic backup created by gedit

---

### Post by buuntuu! on 2007-07-10
it's quite easy. the bootbehaviour can be altered by editing /boot/grub/menu.lst
just open it as sudo with your favourite editor, eg:
```
sudo nano /boot/grub/menu.lst
```
you can change various settings such as the timeout before the chosen os boots...
you'll see these lines:
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

just unqoute the last line (remove #), set the number to the entry that stands for windows on the screen that lets you choose the os to be booted (attention: counting begins from 0, if windows is in 4th place it would boot if default is set to 3) save, exit and you're done.

EDIT: gotta learn to type FASTER!! ;)

---

### Post by uliH on 2007-07-10
Thank you very much indeed for 4 fast and fine answers!!!!

---

