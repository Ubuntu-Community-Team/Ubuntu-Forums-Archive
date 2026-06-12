---
title: "Wine"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Darkblizz on 2007-08-10
so i installed wine and went to install warcraft 3 and now i cannot find wine i did have it under my applications tab but now i do not see it tried to just install it again but it says its already up to date and installed >.> help! where is it lol

---

### Post by bodhi.zazen on 2007-08-10
wine is a command line tool

Or you can add a launcher manually

wine <path_to_program.exe>

---

### Post by bigboy_pdb on 2007-08-10
As bodhi.zazen said, wine is used from the command line. However, there are some useful GUI utilities for wine and they are as follows:

* to configure wine type "winecfg"
* to uninstall a program type "uninstaller"
* to edit the registry type "regedit"
* to view the Windows directory (open the wine file browser) type "winefile"

If you're not certain what the path to the program is then you can use "winefile" to find it (or you could look for it in the "drive_c" folder which is in the ".wine" folder in your home folder). Also, you should put path_to_program.exe in single quotes (i.e. 'path_to_program.exe') because backslashes are escape characters in a Linux command line. Putting a sequence of characters in single quotes makes special characters regular characters.

---

### Post by Darkblizz on 2007-08-12
ok so wine is installed but how to i install something from a CD what do i need to type in the terminal?

---

### Post by zvacet on 2007-08-12
[http://doc.gwos.org/index.php/HowToWine]("http://doc.gwos.org/index.php/HowToWine")

---

### Post by bigboy_pdb on 2007-08-12
Check the contents of the CD (you can do this by double clicking on the icon that appeared on your desktop when you inserted the CD). If you know the path to the executable that you want to run then you can open a command line (Applications -> Accessories -> Terminal) and type "wine **path_to_executable_and_executable**" where **path_to_executable_and_executable** is the path to the executable followed by a forward slash followed by the executable name. For example, if your CD-ROM is mounted to "/media/cdrom/" and the path to the program is "installation/" and the program is "install.exe" then you would type the following:
wine '/media/cdrom/installation/install.exe'

---

