---
title: "Undeletable folder (has padlock and x symbol on it)"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Joe88 on 2007-07-28
I've been having problem getting a HP Deskjet D1360 to work on feisty linux 7.04 using the hpjs driver (which its meant to work with) so i installed a non official HP driver but during the installation it said i had to log off and log in again because i had my printer already plugged in. So i did this but forgot the command i was meant to enter, seeing all the files on my desktop for the installation, i deleted all of them  thinking i could start the installation again and have all the install files not on my desktop (i guess this was a dumb mistake) but one folder could not be deleted and was left over.

It has an x and padlock symbol on it, i have tried deleting it in the terminal as root using the rmdir command but it says the folder isn't empty, when i try and enter the folder as a normal user it says permission is denied and then when i enter it as root it says the cd command was not found.

Does anyone know how i can delete this folder? I would format this PC and start again but I've been setting it up for my grand parents and its meant to be given to them soon so i don't think I'll have enough time to set it up  again.

---

### Post by Paul820 on 2007-07-28
cd to your desktop: cd ~/Desktop and then type in the terminal: sudo rm -R name-of-your-folder. That will get rid of it.

---

### Post by spiderbatdad on 2007-07-28
Have you tried changing permissions on the folder you wish to delete?
sudo chmod 777 (folder)

---

### Post by ron999 on 2007-07-28
If none of those work then try **sudo nautilus** to move it to wastebasket then empty wastebasket.

---

### Post by mkoehler on 2007-07-28
Like Paul said, the following commands will take care of the problem.

```
cd ~/Desktop

sudo rm -r <name-of-the-directory>
```

There is no need for the rmdir command, it doesn't work at all times.  The -r option that is appended to the rm command means 'recursive' - that is, it removes all files and folders inside of that directory.  Good luck!

Cheers!

---

### Post by Joe88 on 2007-07-28
thanks for the help, i managed to delete the folder using the command line : sudo rm -r <name-of-the-directory>
plus i got my HP printer to work using Linux drivers from:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

