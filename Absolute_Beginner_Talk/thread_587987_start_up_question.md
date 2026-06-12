---
title: "start up question"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ughnaught on 2007-10-23
hello ubuntu users, i have a slight problem that i hope one of you might give me some advice on:

I just installed ubuntu to my PC yestarday and everything went very smoothly, and as i expected, whenever i boot up the computer it gives me the option of booting up with windows or ubuntu. this is exactly what i wanted, except that ubuntu is at the very top of this list. you see, my parents and family also use this computer and i dont want them panicking when, after the 10 second timer runs out, they find themselves in ubuntu--possibly unable to figure out how to escape.

what i want to know is if there is a way to switch windows to the top of this list, and ubuntu at the bottom. and also if i can shorten that 10 second timer down to 3 seconds. so that the default choice was windows and they wouldnt have to worry about ubuntu

thanks in advance :)

---

### Post by realvz on 2007-10-23
sudo gedit /boot/grub/menu.lst


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

Change that number to match the entry for Windows in that file.

---

### Post by magli on 2007-10-23
there is also a line in the same file which starts with "timeout" change this number to edit the number of seconds before it boots the default option.

---

### Post by steve.horsley on 2007-10-23
Rather than changing the default list item number, you could re-order the list. Ntice that there is a section in the middle of the file which is marked out as the "automagic" section. Leave that alone, but you could lift the group of lines referring to Windows and move it from below the automagic section to above it. This will make Windows item 0. However, if you are in any doubt about editing this file, just change the default number instead because a mistake in moving chunks around could leave the machine un-bootable.

You should always use gksudo instead of sudo when launching GUI applications, e.g.
**gksudo gedit /boot/grub/menu.lst**
or you could leave applications unable to start in the future.

---

### Post by Major Crash on 2007-10-26
What would one do to remove the timer altogether?

---

