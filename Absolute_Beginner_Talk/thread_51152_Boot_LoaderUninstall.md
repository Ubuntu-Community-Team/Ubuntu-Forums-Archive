---
title: "Boot Loader/Uninstall"
date: 2005-07-22
forum: Absolute Beginner Talk
---

### Post by phil57 on 2005-07-22
Hi,

I have a pc with 3 hard disks in it. One has Windows XP pro, one has Ubuntu and the third is just storage.

I have some questions.

The boot loader Gnu Grub boots to Ubuntu by default. Windows XP is listed under other operating systems in the boot loader window. How can I make Windows the default?

Gnu Grub seems to be loaded into Ubuntu but I can find no trace of it on my Windows system disk and if I try to remove the disk with Ubuntu on it the PC doesn't boot up at all. Is Gnu Grub installed at some lower level in Windows that I can't access?

Can I uninstall Ubuntu from my machine and go back to Windows without reinstalling Windows?

Is there any way I could remove the HD with Ubuntu installed on it to another PC and leave my Windows system functioning in my main machine?

Why is the drive with Ubuntu on it not visible in 'my computer'?

Thanks,

Phil

---

### Post by varunus on 2005-07-22
GRUB is installed into the "Master Boot Record" of your hard drive.  If you want to get rid of Ubuntu completely, you'll need to run the "fixmbr" command from the Windows XP recovery console (should be on your windows install CD).

You can edit your grub configuration in linux to change the default operating system.  Do the following:
Enter "sudo gedit /boot/grub/menu.lst" in a terminal.  Scroll down to the line that reads "default 0" and change it to "default n", where n is the number of the windows entry.  (Each entry counts up from 0, so if windows is the fifth thing the menu, set default to 4.)

Windows cannot see linux drives; Microsoft apparently didn't think windows needed a driver to see linux drives.   :)

---

### Post by phil57 on 2005-07-22
Thanks,

What do you mean by 'in a terminal' in relation to editing boot loader?

---

### Post by varunus on 2005-07-23
Open up a terminal from Applications->System Tools->Terminal.  Then type that command into it.  (It will let you edit files as the superuser so you can modify system files like the bootloader settings.)

---

### Post by phil57 on 2005-07-30
Thanks. I tried opening terminal as suggested and typed in sudo gedit /boot/grub/menu.lst
and hit return. It asked for my password and this brought up an empty window with a tab saying menu.lst but no text to edit. What am I doing wrong?

---

### Post by Larkki on 2005-08-01
You probably made an error while typing. 
You can use the File Browser to see if the menu.lst exists in the /boot/grub folder. (MENU.LST in caps, just to be sure)

Then when you want to edit the file, you can open up the terminal and go one step at a time: 
open terminal.
type "cd /boot"
type "ls" to check if you are in the correct place
type "cd grub"
"ls" to see if the menu.lst is there
"sudo gedit menu.lst"

hope this clarifies a bit.

---

