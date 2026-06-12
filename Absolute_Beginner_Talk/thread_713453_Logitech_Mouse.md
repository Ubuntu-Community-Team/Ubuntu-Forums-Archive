---
title: "Logitech Mouse"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-03-02
Hey there, I have a Logitech MX500 mouse and it has a back and forward button but Ubuntu doesn't recognize this. I tried this tutorial: [http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX500](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX500) but I got really lost. Can someone please give me step by step instructions on how to configure the extra buttons on my mouse?

Really appreciate it.

---

### Post by LuisGMarine on 2008-03-02
Sure, I don't think that this should be too hard.

First of all open up terminal, the first thing we are going to do is make a backup copy of your xorg.conf if anything goes wrong.  Go ahead any copy and paste this command into the terminal and hit enter:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Next, you are going to need to open up the xorg.conf in a text editor to edit the options in for you MX500 mouse.  To do so, copy and paste this command, and hit enter:

```
sudo gedit /etc/X11/xorg.conf
```

Once the config file is up, look for a section that says **" InputDevice " ** when you find that section highlight it and remove it, and replace it with this text:
```

Section "InputDevice"
       Identifier      "mx500"
       Driver  "mouse"
       Option "Protocol"       "ExplorerPS/2"
       Option "Device"         "/dev/input/mice"
       Option "Buttons"        "7"
       Option "ZAxisMapping"   "6 7"
EndSection
```


Hit the save button, and close out of the text editor.  Now you have to restart X, you can just restart your PC , or on your keyboard press **CTRL + ALT + BACKSPACE**.  Doing so will bring you back to the login menu, login and now your buttons should be enabled.  If something went wrong, like something stopped working.  Just go ahead and copy back the old xorg.conf file, like so:

```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

and once again restart X by pressing **CTRL + ALT + BACKSPACE**

Hope this works for ya!

---

