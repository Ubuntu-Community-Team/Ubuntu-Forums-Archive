---
title: "Starting up wine..."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Sporkmaster on 2007-05-05
How do you start up wine? I installed it but can't seem to make it run. What is its terminal command, and do I need to sudo it?

---

### Post by hardyn on 2007-05-05
"wine thewindowsexecutable.exe"

---

### Post by Skandall on 2007-05-05
Open a Terminal window and enter the following at the $ prompt: winecfg

This will setup the virtual c drive as a directory located at:  ~/.wine/drive_c

To install Windows software (which you have to as opposed to running it off an existing Windows partition), download the installer exe to your desktop at: ~/Desktop

Let's say, for example, that you want to install a program called gEngine.  The installer would be located at: ~/Desktop/gEngine.exe

In a terminal window enter the following:
cd ~/Desktop
wine gEngine.exe

This will launch the installer just as you would see on Windows.  Install as normal and use the default install location.

To run the program I have been using the winefile command.  This brings up a file explorer.  Click the C; icon, then navigate to Program Files and fine the application that you installed.

---

### Post by hyperair on 2007-05-06
In ubuntu I believe Wine associated itself with all exe files, so double clicking them would also work, just like in Windows.

---

### Post by ubunter1 on 2007-05-06
i try to run utorrent in wine but i cant open utorrent by double clicking or right clicking on the desktop icon. alternatively i open wine file from the applications menu and navigate to utorrent then open but that wont do it either,any ideas? sorry to troll this thread.:(

---

### Post by zvacet on 2007-05-06
[http://ubuntuforums.org/showthread.php?t=191161&highlight=utorrent]("http://ubuntuforums.org/showthread.php?t=191161&highlight=utorrent")

---

### Post by ubunter1 on 2007-05-06
i just cant get it to open,when i first installed it it worked dling something and was good but now i just cant open it.thanks for that thread though,i guess it will work on fiesty as well.

---

### Post by Enverex on 2007-05-06
Run it from the terminal and see what errors are cropping up. The Gnome menu icon SHOULD work though unless something has gone horribly wrong, which is where running it from the terminal should give you some clues...

---

