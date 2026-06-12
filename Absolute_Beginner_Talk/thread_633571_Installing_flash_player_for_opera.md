---
title: "Installing flash player for opera"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-12-06
Hello i am using 7 10 and i recently removed my firefox and installed opera browser on. While navigating on youtube i found out that it didnt play videos and told me to download this file  install_flash_player_9_linux.tar.gz 

Its so hard for me  to iinstall as it tell me to do it with terminal :

Unpackage the file. A directory called install_flash_player_9_linux will be created.
In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

I DONT KNOW HOW TO NAVIGATE IN TERMINAL I ONLU KNOW CD AND LS THATS ALL, IS THERE ANY WAY FOR ME TO INSTALL THIS MUCH EASIER WAY ?

or a single command or something that i can copy and paste into terminal  would be aprricable, thanks.

---

### Post by fineas on 2007-12-06
Try this:
1) Reinstall firefox and uninstall opera
2) Make sure you have enabled restricted and multiverse repositories (It 's in system>administration>software sources)
3) Using firefox, go to youtube.com and try watch a video. You should be asked something like this 'Do you want to install flash or gnash?". Choose  flash (or gnash if you want so)
4) Reinstall opera

If still nothing,  in a terminal type:

Code:
sudo apt-get install flashplugin-nonfree 

If you still want to unintall firefox, try not to unistall it completely (we want some of its files)

Good luck

---

### Post by daradib on 2007-12-11
Flash plugin installation via repository packages does not currently work. See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

If you get Flash 9 working in Firefox but not in Opera, then try Opera 9.50 (it may be a beta/release candidate) which has better support for Flash 9.

---

