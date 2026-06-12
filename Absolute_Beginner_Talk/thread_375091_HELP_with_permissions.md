---
title: "HELP with permissions"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by ktodac3298 on 2007-03-03
i am using a live cd and i have an old windows 98 harddrive in the computer. when i try to do anything in the hard drive it says i dont have the permissions. I've reformatted to a number of different file systems and it still doesnt work. i need help. specificaly i am trying to dd an image from my external usb hard drive to the old win 98 hard drive. any help would be appreciated.

thank you

---

### Post by tomxyz on 2007-03-03
I'm quite new myself but maybe this info can help.

if you type in a terminal:  df -h
you get information about your system and can see how your hardisk is called.

then you type: ls -l /dev/<your harddisk name, example hda1>
and you see the permissions

then you can type: sudo chmod 777 /dev/hda1 (777, if you want everybody to have access to the harddisk) to change permissions.

you can also type: sudo chown <your username> /dev/hda1 to make yourself owner of the harddisk.

you can also type: sudo chgrp <your username> /dev/hda1 to put the harddisk in your group

type again: ls -l /dev/hda1 to see if your changes are made.

hope this helps

---

### Post by ktodac3298 on 2007-03-03
hey thanks i think it is working. i am not sure because it is just sort of hanging at the dd comand right now but i was told that is what it is supposed to do

---

