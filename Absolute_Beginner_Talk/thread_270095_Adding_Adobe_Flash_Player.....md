---
title: "Adding Adobe Flash Player...."
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-02
Hello!
I know that this gets a bit buggy, and it is known to not work so well in Linux, but I would like to install the Adobe Flash Player plug-in for Firefox. I downloaded it, and unzipped it to my desktop, but being a Linux newbie, I have no clue as to what to do with the resulting file (install_flash_player_7_linux). I hate being a newbie to Linux, but I also hate being stuck in Windows, so any help here would be greatly appreciated!

---

### Post by PPAAUULL on 2006-10-02
Make it executible then execute it.

---

### Post by blendmaster on 2006-10-02
Thanks for the reply!
The problem I'm having is that I can't get the file to run the installer. This is what the read-me file for the plug-in says:

> 
To install the Plug-in Player for Linux via an install script, follow these directions:

- This installer is script-based and cannot be run from a GUI.

- Uncompress install_flash_player_7_linux.tar.gz. A directory called install_flash_player_7_linux is created. Navigate to this directory.
- From the command line, type ./flashplayer-installer to run the installer. The installer will instruct you to shut down your browser(s).

- Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, choose Help > About Plug-ins from the browser's menu.


I type ./flashplayer-installer in the command-line, but I don't get anything. Because the file is on the desktop, I tried to do cd ~/Desktop first, but it still says that there is no such file or directory. Again, any help is appreciated (and thanks for your post)!

---

### Post by PPAAUULL on 2006-10-02
go ```
cd Desktop
cd 'whatever file name is'
./flashplayer-installer 
```
That should get you there, but remember you have to make it executible first.

---

### Post by blendmaster on 2006-10-02
Alright, thanks!
However, while that worked, I've gotta figure somethin' else out now...

---

