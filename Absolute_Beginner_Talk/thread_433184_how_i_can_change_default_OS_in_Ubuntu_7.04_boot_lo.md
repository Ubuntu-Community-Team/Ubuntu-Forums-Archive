---
title: "how i can change default OS in Ubuntu 7.04 boot loader?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-04
Hi
Thank you for reading my post
My linux boot loader boot into linux by default but i want it to boot into windows by default, what i should do to change its behaviour?

thanks

---

### Post by Sef on 2007-05-04
Read [this thread]("http://ubuntuforums.org/showthread.php?t=77024") to change the boot order.

---

### Post by MoxJet on 2007-05-04
Hello.

You need to edit your /boot/grub/menu.lst file. Do:

sudo gedit /boot/grub/menu.lst

You should find a line with

default		0

or another number, change the number to the number your Windows is on, numbering starts from 0. If you don't know which number it has, check further down the file to see which options will be avialable.

Now you need to know where your Ubuntu is saved. In my menu.lst file it says:
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)

It means it is installed to (hd0,1). Exit gedit, and write in terminal:

sudo grub

And you will see a new prompt. Write the following:

root (hd0,1)
setup (hd0,1)
quit

Then, you should be able to reboot your computer and it shall work.
Lots of detailed information about grub is here:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Good luck!

---

### Post by Billy McCann on 2007-05-04
You must edit a file to do this.  The file location is /boot/grub/menu.lst.  

Here is code to allow you to edit this file. "Root" owns the file, so you must gain root privileges using "gksudo".
```
gksudo gedit /boot/grub/menu.lst
```
Copy and paste that into the terminal.  (Applications > Accessories > Terminal)

When you open the file, you'll see a section that looks like this.  

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0
```

Change the 0 to whatever entry Windows is in the list, probably either number three or four.

---

