---
title: "HElp with download"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by AVTOMAT625 on 2007-05-26
Hi everyone i just got linux and am looking to be able to go on Youtube, and while downloading flash i recieved these instructions

# Unpackage the file. A directory called install_flash_player_9_linux will be created.
# In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).


can anyone explain how i go about doing  this?

much appreciated

---

### Post by Happy_Man on 2007-05-26
If you're on Feisty, you can install the macromedia Flash plugin from Add/Remove. That will do it for you, no mucking about needed! :D

---

### Post by Sparkster185 on 2007-05-26
Are you running Feisty?  When I upgraded to Feisty, I simply had to install Firefox and then it was actually able to automatically install the plugin via the Firefox UI.  I didn't have to manually install Flash via command line.

If you really want to try installing it via command line, you're going to need to do a few things.

1) Download the file (I assume it's a tar.gz file)
2) Navigate to the directory where you saved the download
3) type ```
tar -xvfz <FILENAME>
``` where "<FILENAME>" is the name of the file.
4) From there, you should be able to navigate to the directory (usually the same name as the tarball, it should be pretty clear), then just follow the instructions it gave you.

P.S. You might need to run the install script with "sudo" in front of it.

Hope this helps.

---

