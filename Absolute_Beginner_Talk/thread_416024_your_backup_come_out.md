---
title: "your backup come out"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by donamai on 2007-04-20
Hi,

I recently found the GRUB HOW-T0 section so that I could find information on how to change the default OS a the boot up.

I followed the steps on how to change the number in the #set line but I don't think I did it right.

I also followed the steps on backing up the GRUB file before I did this so I am sure I can go back to the way it was before... right?


The problem now is that the computer does not go to the OS I want and the Ubuntu , default OS, does not start... it just says mounting hh8 or something like that and then it gives the command line. Not any clue as to what to do here.

So I come to you guys to ask the following questions:


Where do I go to fix the initiation of the Ubuntu default system?

After fixing it how can I change the from the default OS to the want I want. Most of the instructions in the GRUB HOW-TOs lack on specifying where exactly you have to go to make changes.

Thank you for your help

---

### Post by tbg58 on 2007-04-21
Grub uses a file called menu.lst which is here:
/boot/grub
Before you edit, make a copy by 
sudo cp menu.lst menu.lst.bak (or another file name)

Next, 
sudo gedit menu.lst

If you have just upgraded, you will probably see a fairly long list of OS choices down at the bottom. The most recent kernel version will be up at the top of the list, Windows at the bottom.
Keep the top two versions of Ubuntu, regular kernal and recovery mode, then delete the ones down to the mem test.  Leave mem test and the divider for other OSes, and leave Windows.

Back up in the upper part of the file, set the default value to 0
default=0 
to boot the first Ubuntu version you see.
Count from the top one down to Windows to find the number of windows -- starting from zero.
If you want to default boot to Windows, set that number.
This should get you going.
Hope this helps.

Good luck!

-Rob

---

