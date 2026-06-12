---
title: "flash player on 64 bit/"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-28
ok i might sound like a dumbass but i can do this!!!!! i did what flash told me to do

> 
Installation Instructions

1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.



and this is what came up

slave@slave3:/tmp/flash7$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
Macromedia Flash Player installer.

does this mean there is no flash player for 64 bit???? im a myspace user and without flash its useless.....

can anyone help????

---

### Post by pay on 2006-12-28
You can use nspluginwrapper to install 32bit plugins with a 64bit browser or you can install a 32bit browser with a 32bit plugin. Read this for the latter [http://www.ubuntuforums.org/showthread.php?t=202537&highlight=flash+64bit](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=flash+64bit)

---

### Post by antgul3382 on 2006-12-28
thanks pay your the first help ive gotten thaat worked!!!!!

---

