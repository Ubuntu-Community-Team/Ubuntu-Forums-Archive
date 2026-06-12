---
title: "Desktop Link Not Functioning"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Spartnova on 2008-03-27
First, please note, I am entirely new to Ubuntu and Linux (except for 4 day attempt in 1999 to make Corel Linux work).  I have not even used the Terminal.  Here is my issue:

I installed Alien Arena 2008 and it runs fine if I double-click the crx.sdl file within the folder I have set up for Alien Arena.  However, I cannot get a desktop link to work.  I have tried both i) the Create Launcher option on the desktop and ii) creating a launcher by adding an entry under "Edit Menus" (right click on Applications tab) and then selecting the "add this launcher to desktop" option  once Alien Arena is in the menu by right clicking on the new entry.  Regardless, once I double click on the new icon on the desktop, nothing happens.  I have used the same method on manual installs of Songbird and Nexuiz with success, but Alien Arena is not working.  

Why is this happening?  Permissions?  Thanks for your help!

---

### Post by Hospadar on 2008-03-27
probably the issue is that by default, desktop launchers run the program in your home directory, and I would guess the alien arena executable needs to be run in the alien arena directory.

What you'll have to do is create a script to change directories and then start the program.

the easiest way to do this is by terminal Applications->Accessories->Terminal

First go to your alien arena directory, then create a script, and make the script executable.
```
cd /home/<your username>/alien_arena_or_wherever_it_is
nano startscript.sh
```Now add this to the new text file```
cd /home/<your username>/alien_arena_or_wherever_it_is
./<name of the executable>
```Ctrl-O to save, Ctrl-X to exit
Now make the file executable```
chmod +x startscript.sh
```Now try making a shortcut to that script we just created and see if that works.

---

### Post by Spartnova on 2008-03-27
Hospadar:

Sounds logical.  I will give it a try when I get home tonight.  Thanks!

---

### Post by Spartnova on 2008-03-31
Worked like a charm!  For newbies experiencing the problem with Neverwinter Nights, the same script worked.

Thanks again!

---

