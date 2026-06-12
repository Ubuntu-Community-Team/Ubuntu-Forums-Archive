---
title: "Where is SPM putting the package?"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by iamtaylormade on 2005-10-29
23 years of computers and very little LINUX based stuff, love it so far but need to get up to speed. Too much time researching and not enough time making progress.
This is an easy problem for someone out there, I am just too ignorant as to how the OS operates and can't seem to find a specific answer in the forum (probaly a poor choice of search terms).

I have used the SPM to "download" packages/programs/utilites and they show in SPM as "installed" (rebooted twice) but do NOT show in any of the menus (GUI) and I cannot find the directory/location where they were installed (is there a default). Examples would be procmai, smartmontools, wireless-tools, nvidia-settings and a nice FTP program that I forget the name of unfortunately.

I would like to use these "tools" but cannot navigate to their locations.
Are they just CLI tools or GUI(I know the FTP tool is GUI), are they really installed, if so, how do I utilize them?
Sorry for the ignorance...

Thanks in advance.
Breezy Badger 5.10/64/XPpro/2000Serv/ w/AMD64 3200/1TB SATA RAID/80GB SATA w/OS's

---

### Post by sas on 2005-10-29
If it's a GUI tool and it doesn't appear in any of the menus (applications, places, system) or in the "add to panel" dialogue (right click on a panel and press add) then it's a bug, 

You should go to [https://launchpad.net/distros/ubuntu/breezy/+filebug](https://launchpad.net/distros/ubuntu/breezy/+filebug) and fill out a form to let the developers know.

You can find out where the application is installed by typing which <app name> in a terminal window.

Then if you go to the menu editor (applications > system tools > Application Menu Editor) and go to File > New Entry you can add it to your menu.

I don't think any of the programs you mentioned are GUI tools though.

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=iamtaylormade]23 years of computers and very little LINUX based stuff, love it so far but need to get up to speed. Too much time researching and not enough time making progress.
This is an easy problem for someone out there, I am just too ignorant as to how the OS operates and can't seem to find a specific answer in the forum (probaly a poor choice of search terms).

I have used the SPM to "download" packages/programs/utilites and they show in SPM as "installed" (rebooted twice) but do NOT show in any of the menus (GUI) and I cannot find the directory/location where they were installed (is there a default). Examples would be procmai, smartmontools, wireless-tools, nvidia-settings and a nice FTP program that I forget the name of unfortunately.

I would like to use these "tools" but cannot navigate to their locations.
Are they just CLI tools or GUI(I know the FTP tool is GUI), are they really installed, if so, how do I utilize them?
Sorry for the ignorance...

Thanks in advance.
Breezy Badger 5.10/64/XPpro/2000Serv/ w/AMD64 3200/1TB SATA RAID/80GB SATA w/OS's[/QUOTE]

The properties tab under SPM will show you where all the files associated with the package were installed.  Or from the terminal ```

$ dpkg -S 'package-name'

```

---

### Post by The Mekon on 2005-10-29
Perhaps I am missing something here.  Can't you type "whereis packagename" or "locate packagename" in a terminal?

Brian

---

### Post by Mustard on 2005-10-29
I know for sure that nvidia-settings can be run by entering..

```
sudo nvidia-settings
```

in a terminal.

It sounds like you may not be too familiar with the use of the terminal.  It may be useful for you to know that when you install stuff using synaptic, all the binaries for the file you installed go in the same directory, so your linux operating  already knows where they are, because it put them there. In a general sense, all user installed applications will end up in the /usr/bin directory.  This is why you normally only have to enter the name of the program into terminal and hit enter (sometimes you need to put a 'sudo' command in front of the name if the program needs administration privileges to run, as nvidia-settings does).  Another feature that people new to linux don't always realise is available in terminal, is that you can type part of a filename in and then hit the TAB key and it will autocomplete the rest of the name.  If there is more than one choice for autocompletion, then you can hit TAB again, and it will list ALL the choices.

As mentioned earlier you can add items to the menu, using Applications>System Tools>Application Menu Editor (this is its location in Breezy anyway, for Hoary you will have to download SMEG), but this still requires that someone new to linux actually knows what to put in the little boxes to make the program run. Generally all you have to put in is the name of the application in the 'command' field.  If you look at some of the other entries in the menu editor, by selecting them, right clicking and choosing properties, you can see how all the other applications are loaded up.  Some applications will have entries in the menu after installation and some won't, its just the way they are setup.

You might try reading over these links to understand some basic terminal commands.

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

I'd also recommend installing nautilus-open-terminal through synaptic, as it allows you to open a terminal using your 'context menu' when you right click somewhere on desktop.  I find going up to the menu to choose terminal a bit laborious myself.

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=The Mekon]Perhaps I am missing something here.  Can't you type "whereis packagename" or "locate packagename" in a terminal?

Brian[/QUOTE]
"whereis" "which" and "type" only work if you know the command name, which is not always the package name (e.g. image-magik).

---

### Post by iamtaylormade on 2005-11-01
Thanks to everyone that replied.  I appreciate all of the assistance.  I got those problems and a few others squared away.

This OS is brilliant!

---

