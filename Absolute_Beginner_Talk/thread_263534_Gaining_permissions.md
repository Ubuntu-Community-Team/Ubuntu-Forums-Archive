---
title: "Gaining permissions"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by nawyner on 2006-09-23
Sorry for even asking this.  I am a complete Ubuntu/Linux newbie (installed yesterday and have been playing with it as an alternative to windows) Anyway for the time being I still need windows to be the default boot.  Now I changed the grub file but it is not letting me save it because it says I don't have proper permissions.  How do I get those permissions?

---

### Post by benuski on 2006-09-23
If you edit the grub file by going to the command line and typing "sudo gedit" and then the file name and then type in your password when prompted, that file will show up and then you will be allowed to save.

---

### Post by nts on 2006-09-23
press Alt-F2 and type gksudo nautilus to open a new window with *temporary* root permissions.

Root is unavailable by default, use 'sudo' in a terminal before a command such 'sudo apt-get install gaim' to gain root permissions. 

I hope this helps

---

### Post by ewl1217 on 2006-09-23
Just run the editor of your choice from the terminal prefixed with the command sudo (for text-based apps) or gksudo (for graphical apps). So to edit it from the terminal use the command
```
sudo nano -B /boot/grub/menu.lst
```
or to edit it with a graphical editor use
```
gksudo gedit /boot/grub/menu.lst
```
Just use caution in editing this, since it is an important system file. The nano command will make a back-up for you (that's what the -B option is for), but you'll have to do that manually with gedit.

---

### Post by nawyner on 2006-09-23
Thanks guys,  THat seems to have worked.  I am still getting used to all this command line/ terminal stuff.  I have been inendated w/ windows and I am sick of paying their outrageous fees for stuff.  Anyway, expect more dumb questions but I must say I have learned a lot in the day I have been messing with it.

---

### Post by Sef on 2006-09-23
> expect more dumb questions

You did not ask a dumb question.  We welcome all intelligent questions like yours.

---

