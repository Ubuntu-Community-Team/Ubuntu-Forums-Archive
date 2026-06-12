---
title: "Installing Cycas 3.2 evaluation version"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by paulji on 2006-07-20
I downloaded cycas_en-3.20-1.i386.tar.gz to my desktop.
Opened the cycas_install_en onto my desktop.
Double clicking cycas_install-en opens the file browser.
Double clicking Cycas3_install opens dialog box.
Clicking run in terminal takes me to: a prompt that reads:
Location to install the Cycas directory [/usr/local]:
Hitting enter I get the message:
"Wrong path or missing write permission.
Please give a valid directory name."
The actual instructions are in the read me file below. Being a
newbie I don't really understand the instructions. Maybe some steps are missing?

Can anyone explain what I need to do to accomplish the install? 

##### Installation #####

- switch to root.
- 'cd' into the installation directory.
- type "./cycas3_install"
- follow the instructions.

The installer will  ask you  for the installation path. 
(Default is "/usr/local/".) A "cycas3" directory   will
be  created   there,  containing  the  program and  all 
data files. 

Some CYCAS startscripts will also be created and placed
in /usr/local/bin:

/usr/local/bin/cycas3
/usr/local/bin/cycas3_verbose
/usr/local/bin/cycas3_deinstall

The Installer will  detect your  Gnome or  KDE -Desktop
automatically and will  install  a menu  entry  in your
Applications menu.

The Desktop needs to be restarted to  activate the menu
entry.

---

### Post by slimdog360 on 2006-07-20
open a terminal window and copy
```
cd Desktop
sudo ./cycas3_install
```
then once that has finished log out and log back in, or alternatively press ctrl+alt+backspace.

---

