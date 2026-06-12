---
title: "How do I turn ACPI off?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by mrgreg on 2008-01-21
I am trying to turn off ACPI in grub, but after I enter the code acpi:=Off noacpi, and go to save I get an error that say can't open file to write. I am running Xubuntu 6.06 on an IBM think Pad 600e. I just made the switch from windows... any help here would be great. :confused:

---

### Post by logos34 on 2008-01-21
gksudo gedit /boot/grub/menu.lst

add **noacpi** to end of '**# kopt=...**' line.  Then run **sudo update-grub**

---

### Post by banewman on 2008-01-21
As logos34 said - open a terminal (in the menu under applications - accessories - terminal) and type that command - give your password - and the file will open to let you edit it and save changes.
:)

---

### Post by mrgreg on 2008-01-21
Ok, I typed in the command it prompted for my pass word... but now it just sits there and does not a thing... no menu?

---

### Post by banewman on 2008-01-21
Sounds like turning acpi off wasn't the thing to do - what are you trying to get/stop working?

---

### Post by mrgreg on 2008-01-21
I am trying to turn ACPI off so that it will let my wifi card work. With it on, I have read that it does not alow them to work  on the thinkpads.

But the command you told me to use is not bring up any menu for me to edit... is there another way to edit the line command?

---

### Post by njparton on 2008-01-21
Have you tried the bios?

---

### Post by logos34 on 2008-01-21
> **mrgreg said:**
> 
But the command you told me to use is not bring up any menu for me to edit... is there another way to edit the line command?

**sudo nano -w /boot/grub/menu.lst**

---

### Post by banewman on 2008-01-21
Try -
sudo nano /boot/grub/menu.lst
that should give you an editable file if you have admin rights(do you have admin rights?)
The controls for the prog are at the bottom
:)

---

### Post by mrgreg on 2008-01-21
I type in sudo nano -w /boot/grub/menu.lst, it then prompts me for my password I enter it then it does the same thing as before. I try to reenter the command then it tells me command not found????

---

### Post by njparton on 2008-01-21
Turn acpi off in the bios.

---

### Post by mrgreg on 2008-01-21
that should give you an editable file if you have admin rights(do you have admin rights?) 

I put the OS on the laptop set the user name and password... It would be the same password that I log in with... so I assume that I have admin rights.

---

