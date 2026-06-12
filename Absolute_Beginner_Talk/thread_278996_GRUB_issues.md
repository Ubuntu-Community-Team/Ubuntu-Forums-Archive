---
title: "GRUB issues"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Irisher on 2006-10-17
I have a VAIO UX180P and attempted to run UBUNTU from a seperate USB HD.  Now the issue I ran into is this...  The instal runs smoothly up till the first time you have to restart.  Just before you restart the installer will ask if you want to install the GRUB utility to the master boot record so that you can pick and choose which OS you want to use.  But when the computer restarts it comes up with the message GRUB loading please wait and then it says Error 21.  I am stuck.  Is there a way to undo the change to the master boot record so that I can at least still use my computer?

---

### Post by Kateikyoushi on 2006-10-17
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restart the computer.

---

