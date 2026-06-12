---
title: "Ahhhhhh! Grub Is Gone!"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-10
I don't know what has happened but grub has gone and I can only boot into Windows!!  :shock: :frown: 

Is there anything I can do to install grub so I can boot Ubuntu?

PLEASE SOMEONE SAY YES!!  I hadn't yet done a backup of Ubuntu.:cry: 

Russty

---

### Post by Russty of Oz on 2006-09-10
It's OK, false alarm!

I managed to get windows to do a restore of the computer and somehow it has returned grub as well!?  I don't care how it did it, I am just GRATEFUL that it has.:D 

PHEW!! That was a close one.  **I MUST DO A BACKUP NOW!**[-X 

Russty.

---

### Post by rbmorse on 2006-09-10
You might also want to get the supergrub package. There is an .ISO file that builds a self-booting CD you can use to rescue and recover GRUB in the future if necessary.

---

### Post by bulldog on 2006-09-10
If you have the live cd I can give you the way to reinstall grub from there.
Copy and paste it and print it out :D 
Here it comes.

This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)


Finally exit the grub shell
Code:

quit

Don't forget to alter your menu.lst AND your fstab!!!! 


That is it. Grub will be installed to the MBR.

---

### Post by Russty of Oz on 2006-09-10
Thanks guys!

That will be very useful in the future I am sure.  I seem to be able to screw things up without even knowing that I am doing anything wrong.  

Thanks again for that help.

Russty.:)

---

### Post by Russty of Oz on 2006-09-13
> **bulldog said:**
> 
Don't forget to alter your menu.lst AND your fstab!!!! 


That is it. Grub will be installed to the MBR.

Hmmm, what is the "menu.lst and fstab" and how and what am I suppose to do with them?

Russty.

---

