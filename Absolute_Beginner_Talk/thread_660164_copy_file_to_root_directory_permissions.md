---
title: "copy file to root directory permissions"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by matadams on 2008-01-06
i recent installed cairo-dock. i'm trying to install themes and it says to put them in the .cairo-dock directory, (which i can't find and i've searched for) 
also, i'm supposed to put some files in the opt directory. but when i try and copy them there it says i don't have permission.

i've tried giving myself permission in the users/group menu. but nothing helps. i tried logging in as root and it says you can't login as root on that screen.

then i tried using the terminal, (which i don't know well) i use sudo. but no matter what i type is says there's no such file.

i'm just trying to copy files from my desktop to the folder opt/

is there an easier way to do this?
and how do i find the .cairo-dock folder?

thanks.
mat

---

### Post by philinux on 2008-01-06
Goto your home folder and type ctrl H any .xxx. folder are hidden.

Use ```
gksudo nautilus
``` to copy files to opt

---

### Post by mcduck on 2008-01-06
.cairo-dock is a hidden directory inside your home directory. Files and directories with a name starting with a dot are considered as hidden files in Linux. To see them in the file browser just hit Ctrl-H (or enable them from the settings dialog).

To manage files outside your own home you need root permissions. In Ubuntu they are handled with the 'sudo' command: [https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29")

The simple answer is to start the file manager as root: hit Alt-F2 and run 'gksudo nautilus'. Remember to close the window as soon as you donm't need it any more, as it allows you to delete anything from your system and that makes it dangerously powerful tool..

Also note that both the window you are copying from, and the window where you are copying to, need to be running with root privileges. So after opening the first window go to File/Open New Window to open another one. Then you can use those to copy your files into /opt.

(I always set the root Nautilus to have a red background to make sure I never mix it with Nautilus running as my own user)

---

### Post by matadams on 2008-01-06
thank you, you guys are awesome. i appreciate the fast response!
mat

---

