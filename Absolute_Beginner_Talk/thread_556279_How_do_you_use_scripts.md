---
title: "How do you use scripts?"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by NorthernPaladin on 2007-09-21
Ok, I want to mount an image, and I found a script for it [http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369) . The problem is, I do not know how to use scripts. Could somebody tell me what to do?

---

### Post by ddrichardson on 2007-09-21
Generally, you just set them to be executable and run them: from a terminal:```
chmod +x scriptname
./scriptname
```

---

### Post by erfahren on 2007-09-21
just copy them and paste in seperate text files. name the first one "nautilus-mount-iso" and the second one "nautilus-unmount-iso" 

save them to ~/.gnome2/nautilus-scripts/  (which is your /home/<username>/.gnome2/nautilus-scripts/  ) and set them to be executable

-- you can do all this through the GUI
~/.gnome is a hidden folder so open up your /home/user folder and press Ctrl+H

create the folder "nautilus-scripts" in there if it doesn't exist

paste the two files into there

set them to execute by right-clicking on each one and select Properties > Permissions tab and check "Allow executing this file as program"

Probably need to restart X (Ctrl+Alt+Backspace)

Now when you right-click on the .iso a selection "Scripts" should show in the menu, and under it will be the two scripts

------------------------------------------------------------------

terminal way

just look at this tip in the Wiki for "Open as root" - same basic thing -- you'll see

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_open_files_as_root_user_via_right_click](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_open_files_as_root_user_via_right_click)

by the way: in that tip the file name is entered as "Open\ as\ root" - the "\" is just a switch telling bash to ignore the following space 
(so the script will show up as "Open as root" in the menu)

--- another note
you can create a folder named "bin" in your $HOME folder and make your own shell scripts and stick them in there
you can then run them in the terminal by just typing it's name (bash will look for scripts in that folder)

see here for more info on shell scripts: [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

---

