---
title: "[SOLVED] How Do I Change the Boot Record?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by acelin on 2007-09-11
I have to edit the boot options everytime I boot onto my external HD that has Ubuntu...

How do I change this where it will boot with out editing - it needs to be changed from "root  (hd1,1)" to "root  (hd0,1)"

how do I do this and what if the file that needs changing says I dont have root permission?

---

### Post by Beowulf.1000 on 2007-09-11
Boot into your Ubuntu, then open up a terminal.  
$  sudo su
#  grub
  > root (hd1,1)
  > setup (hd0)
  > quit
# exit
$

root (hd1,1) tell Grubs that the linux root and kernel are on hd1 and the first partition. This is common when for example MS-Windows is on hd0 (/dev/hda or ide0) and Linux is on a second IDE drive such as hd1 (/dev/hdb or ide1).

setup (hd0) tells Grub to install the bootloader to hd0.

You do not type the $, #, or >, those are command prompts. The 'sudo su' command puts you into root admin mode, but of course you will be asked for your root or admin password that you need to provide. Then, once in the root command prompt (#) you type the grub command to enter the Grub shell which has '>' as its command prompt. Type the three grub commands as indicated above (root, setup, quit).

If you currently have linux on hd1 then you do not want to change the root() command to root (hd0,1) unless you actually have a linux distro with its root and kernel image residing on hd0.  Think out what is where, where you want to put the bootloader.


> **acelin said:**
> I have to edit the boot options everytime I boot onto my external HD that has Ubuntu...

How do I change this where it will boot with out editing - it needs to be changed from "root  (hd1,1)" to "root  (hd0,1)"

how do I do this and what if the file that needs changing says I dont have root permission?

---

### Post by markp1989 on 2007-09-11
> **acelin said:**
> I have to edit the boot options everytime I boot onto my external HD that has Ubuntu...

How do I change this where it will boot with out editing - it needs to be changed from "root  (hd1,1)" to "root  (hd0,1)"

how do I do this and what if the file that needs changing says I dont have root permission?


type "sudo gedit /boot/grub/menu.lst" in the terminal, and then it will ask for your user password. and you can make the changed you need there

---

### Post by acelin on 2007-09-11
I figured it out- thanks though... I will mark as solved.:guitar:

---

### Post by rfurman24 on 2007-09-12
> **acelin said:**
> I figured it out- thanks though... I will mark as solved.:guitar:

You should probably tell what you did to solve your problem so others can learn from it.

---

### Post by acelin on 2007-09-12
In terminal type:

gksudo gedit /boot/grub/menu.lst


then go down and edit the root (hd1,1) 

change it to:

root (hd0,1)


:guitar:

---

