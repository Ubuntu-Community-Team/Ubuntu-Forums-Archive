---
title: "Help with GRUB Splash screen"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by S{yndrom}e on 2006-05-04
Hi i recently downloaded a splash screen for the GRUB loader from gnome-look.org

Now it says to copy the xpm.gz file to /boot/grub. But when i try to do that it says that i can't: I don't have permission. Is there a sudo command that lets my copy files or is there another way?

Thanks for all the help.

---

### Post by dave9191 on 2006-05-04
The /boot folder is only accessible as root. So if you try to put stuff there as your regular user it wont let you. Sudo allows you to run root commands. You can either do this on the command line or with a graphical program. 

Graphically open a terminal and type 

sudo nautilus

This will start the file browser as root so you can move the files. Alternativly you can copy the file on the command line usign (assuming the file is in the current dir):

sudo cp xpm.gz /boot/grub

Hope that helps, 

--
Dave

---

### Post by S{yndrom}e on 2006-05-04
Yay thank alot it worked!
And Now i also know about that root-file browser thing :) 

Thanks alot

Edit: Opps sorry again but i have another problem. I am supposed to edit a file called menu.lst. I opened it with gedit and tried to edit it. However, when i type nothing is printed. 

Could you please help me again, I am so sorry for all the trouble.

---

### Post by opticyclic on 2006-05-04
What you want is GrubConf
It allows you to make all the changes via a GUI
e.g. you can select the splash image via a dialog and you can select/deselect O/Ses to boot with the mouse.

Much easier!

---

### Post by S{yndrom}e on 2006-05-04
K thanks googling for it now =)

And i think I also found a work-around. It seems if i move the menu.lst files out of /boot/grub i can edit it. So ill save after ill edit it and then move it back to /boot/grub via nautilis. Well thanks everyone for everything!

---

### Post by hanexar on 2006-05-04
You need to be root to edit the file.

Try

```
 sudo gedit /boot/grub/menu.lst 
```

You can probably edit it now.

Good luck!

---

### Post by dave9191 on 2006-05-04
You can't edit the file where it is because the editor you are using is running as your unprivilaged user. If you open the root file browser and click to edit the file, the text editor should be started as root and you will be able to make changes. But copying it back later or as hanexar said "sudo gedit filename" also works :)

--
Dave

---

### Post by hanexar on 2006-05-05
Wow, that was way more clearer than I was!

---

