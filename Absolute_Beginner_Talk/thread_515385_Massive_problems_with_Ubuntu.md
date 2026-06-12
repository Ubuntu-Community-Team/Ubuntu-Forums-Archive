---
title: "Massive problems with Ubuntu"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by butterandguns on 2007-08-01
Okay.
So I installed Ubuntu on my laptop.  This is Ubuntu Ultimate Edition from ubuntusoftware.info .  After the install it asked me to get the Nvidia driver which I did.  Then there were 148 files that needed to be downloaded in an update.  I restarted after that.  And now ubuntu won't load at all.  It says that I have some problem with my xorg.conf and takes me staright to a terminal.  I had decided to get rid of windows entirely so now can't go back because I have no windows CD.  So now it is Ubuntu or nothing.  So I have 2 questions. 

1) What can I do to fix this? (Any instructions need to be in simplest terms possible)
2) Is this a problem I would not face with regular Ubuntu 7.04?  In other words should I try to install just the regular Feisty Fawn?  I like all the options that came with Ultimate Edition but if it is a choice between Regular Ubuntu and no OS I'll go with regular Ubuntu.

Any help would be appreciated. I need to have this computer up and running in 10 days.  Thank you so much.

---

### Post by splintercellguy on 2007-08-01
Annoying thing about Nvidia/ATI drivers: when you get a new kernel, you have to rebuild. Envy might help you here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by wolfen69 on 2007-08-01
i do love ubuntu ultimate as a live cd, but as a personal preference, i would go with regular ubuntu and add what i need. if you do go with regular feisty and want to make things easier on yourself, install automatix after.(no flames please) [http://getautomatix.com/](http://getautomatix.com/)

---

### Post by butterandguns on 2007-08-01
I installed the Nvidia drivers using Envy.  
WHen I restarted it said there was a poblem with xorg.conf.  Now Ubuntu doesn't load.  It takes me straight to a terminal prompt.

I am currently using Ubuntu from a live cd as I have no OS on this computer and no other computer to use.

---

### Post by asmoore82 on 2007-08-01
using the liveCD,
find the file "/etc/X11/xorg.conf" on your hard drive - not on the LiveCD
and find and replace the text 'nvidia' with 'nv'

this should get your actual install back up and running on the free nvidia drivers.
or at least give you a better error :lol:

---

### Post by Moop on 2007-08-02
If envy is installed then I think you just need to run ```
sudo envy -t
``` from the terminal.

---

### Post by butterandguns on 2007-08-02
Okay cool.
Ubuntu is working now.  Well sort of.
I can now log into it and use the internet and such,
New problem.
Nothing I download appears on the desktop and I am unable to open my home folder.  I click on Home Folder int he Places menu and the taskbar says "Opening Home Folder" for a few seconds then dissapears.  I am downloading files to the desktop but none are appearing there.
Help again.  You guys have been great so far.

---

### Post by Frak on 2007-08-02
Note to others that can help, it sounds like Nautilus isn't drawing the desktop, nor is it listening to the Gnome-Panel. I don't know how to fix this, but hopefully someone else does.
EDIT
Run the terminal
```
cd ~/Desktop
ls
```
And paste the output.

---

### Post by butterandguns on 2007-08-02
> **Frak said:**
> Note to others that can help, it sounds like Nautilus isn't drawing the desktop, nor is it listening to the Gnome-Panel. I don't know how to fix this, but hopefully someone else does.
EDIT
Run the terminal
```
cd ~/Desktop
ls
```
And paste the output.

Output
fr.6629.0.nsplugin-wrapper-install-0-1.1-diagnose.tar
FretsOnFire
install_flash_player_9_linux
nsplugin wrapper install
nsplugin-wrapper-install-0-1.1-diagnose.tar.gz
Upgrade.desktop


As you can see, there are files on the Desktop.  But they do not appear on the actual desktop.  I'm pretty new to Ubuntu so I can't navigate through the terminal and need the desktop.

---

### Post by butterandguns on 2007-08-02
bump

---

### Post by Frak on 2007-08-02
Hmm... I don't think many recommendend this, but I want you to do an X restart and see what happens.
To restart X, do Ctrl+Alt+Backspace
And see if things start to "reappear"

---

### Post by butterandguns on 2007-08-02
Did ctrl+alt+backspace.  Still nothing on the desktop,

Don't know if this helps but I was searching through the forum for people with similar problems and saw someone suggest "sudo nautilus"
I tried it and it opened up a filebrowser.  If i navigate back to the root menu and open up the home folder from there I have access to it and can even look at my desktop in a window.  But not on the actual desktop.  All the files are there but still invisible on the desktop as you can see on the attached sreenshot.

---

### Post by Tux Aubrey on 2007-08-02
I don't want to be a party pooper, but, despite the name, Ubuntu Ultimate is not an official version and its hard for general users of official versions to know all the details of how TheMahn2003 set it up.  We could easily lead you astray.  It has a lot of scripts and additional features that may be part of the issue you are experiencing.

I'd suggest you ask him and other UU users more directly by posting in this thread:

[http://ubuntuforums.org/showthread.php?t=461378]("http://ubuntuforums.org/showthread.php?t=461378")

(This is not to say that any of the responses you have received here are not correct)

---

### Post by butterandguns on 2007-08-02
Okay.  So I posted in the UU thread.  But just in case it is a general Ubuntu problem and not a UU specific problem I would still love it if you guys could help me more.

---

### Post by Frak on 2007-08-02
We'll be here, I don't plan to leave anytime soon :)

---

### Post by asmoore82 on 2007-08-02
open  a terminal and run these commands

```

asmoore@asmoore-laptop:~$ gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true
asmoore@asmoore-laptop:~$ killall nautilus
asmoore@asmoore-laptop:~$ nautilus &>/dev/null &
```

---

### Post by butterandguns on 2007-08-02
Okay.
I don't know what I did.
I just went into the xorg.conf and chose more screen resolutions and when I reloaded ubuntu my desktop was back and everything is perfect.
Thanks for all the help guys.

---

### Post by vexorian on 2007-08-02
:/ my experience with .info sites has always been negative

---

### Post by Frak on 2007-08-02
Thanks asmoore for helping on this thread :)

---

