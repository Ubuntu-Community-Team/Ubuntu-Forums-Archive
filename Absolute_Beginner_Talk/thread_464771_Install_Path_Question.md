---
title: "Install Path Question"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by sw1995 on 2007-06-05
Hello!

I've been doing some reading in an attempt to figure this out for myself, but it is time to ask a question:

I am curious to know a bit about correct installation paths; for instance:

I have Google Earth installed in my home folder simply because that was the default installation path offered by the GUI. Using Windows, for instance, I would generally install a program such as Google Earth in the "Program Files" folder--is there a close equivalent to such a folder in the Linux File system or is my thinking still way too Windows-based here?

I would rather not gunk up my home folder and I have read that the /usr/local/bin directory is an appropriate place for such things (although I suspect that it cannot be that easy of a solution) but when I tried to change the path the GUI told me that the directory did not have the proper write permissions.

Is it possible to simply move the folder to another directory using the terminal? I have noticed that when I hide the folder by adding a "." to the file name, the desktop icon ceases to function.

Does this make any sense?!  Thank you in advance for any help!

-S

---

### Post by kevdog on 2007-06-05
Why dont you just store the files in /home/*username*/bin??

Check to see if this in in your path.  Just type $PATH at command line, I believe it is the first entry.  If not you can modify the path statement in either .bashrc or .bash_profile.

---

### Post by RomeReactor on 2007-06-05
Hi. Installing programs in your home directory is perfectly fine; it's only when there are multiple users on your PC that it would be a good idea to install it in /usr/local, so everyone has access to it. To install on that folder, you would need to launch the installer as root (using **sudo**). As to the desktop icon ceasing to work, it's because hiding the folder (by placing a period in front of the name) also *changes* the name of the folder, so the icon has to reflect that change (you can change the path to the program by right-clicking the icon and selecting "Properties".

EDIT: If you want to keep your homefolder clean, you can try making a hidden folder where you install all your games (**/home/YOU/.games**, for example), and point the installers to that folder.

---

### Post by sw1995 on 2007-06-05
Perfect; thank you for your help!

-S

---

