---
title: "Help!!!"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Tdycrazy6 on 2006-11-22
Hey,
 I just installed ubuntu 6.10 to dual boot w/ osx and I want osx to be my default operating system. i read 'man yaboot.conf', but when i add 'defaultos=macosx' to 'yaboot.conf'. It says that I do not have permission to save this file. i guess its a read-only file. How would i make my defaultos be osx? :confused:

---

### Post by Ecthelion on 2006-11-23
> Hey,
I just installed ubuntu 6.10 to dual boot w/ osx and I want osx to be my default operating system. i read 'man yaboot.conf', but when i add 'defaultos=macosx' to 'yaboot.conf'. It says that I do not have permission to save this file. i guess its a read-only file. How would i make my defaultos be osx? 

Hi,

do you use the grub bootloader to choose which operating system to start up?
If you do, you just have to change a number in /boot/grub/menu.lst :
```
sudo gedit /boot/grub/menu.lst
```

Look for this line
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default		0**
 
And change the 0 to the number your other OS is on.
If you don't know, just scroll down to where you can see the entries of the grub menu and count from the first option to the option you want to start up (start counting from 0)

Then save the file and that's it!

I hope this helps...

---

