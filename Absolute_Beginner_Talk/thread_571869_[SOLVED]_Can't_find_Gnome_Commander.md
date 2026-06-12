---
title: "[SOLVED] Can't find Gnome Commander"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-09
I installed Gnome commander through Synaptic but could not find it on my menus. So I uninstalled it and reinstalled it from Applications/Add-Remove. However, I still can't find it on any of my menus.

No doubt I'm missing something obvious, but I have had Ubuntu for less than a week, and I am a Windoze refugee, used to things like xplorer2 and Powerdesk.

Any suggestions how I can find and run Gnome Commander to test it out?

Regards,

Alan

---

### Post by Dr Small on 2007-10-09
Never had it, but did you try typing the name of it in the terminal ?

---

### Post by Shazaam on 2007-10-09
Reboot. If still not there open terminal and input 
```
gnome-commander
```
and see what happens.

---

### Post by llamakc on 2007-10-09
Unless it hooks itself into boot scripts, there's rarely a reason to reboot after installing a package.

You can see WHAT files are installed with any package by opening a terminal and typing:

dpkg -L gnome-commander

Or, you can search at [http://packages.ubuntu.com](http://packages.ubuntu.com) and you'll get something like this (after choosing the architecture you're running at the bottom of the page)

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-commander&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-commander&version=feisty&arch=i386)

Looks like the command is:

gnome-commander

You can either type that in a terminal or type ALT-F2 and enter it there.

---

### Post by Alan Stancliff on 2007-10-09
Thank you, Dr. Small, Shazaam, and llamakc. All that information provides me with new things to think about. 

As it turns out, when I rebooted, I found the Gnome Commander. So far it looks great.

---

### Post by Dr Small on 2007-10-09
A reboot wasn't neccessary. All you most likely needed to do, was restart X.
[CTRL + ALT + SHIFT + BACKSPACE]

---

### Post by RomeReactor on 2007-10-09
Most of the time just restarting the gnome-panel will do.

---

### Post by Shazaam on 2007-10-09
> **RomeReactor said:**
> Most of the time just restarting the gnome-panel will do.
I know the ctrl+alt+backspace command but how do you restart the panel?

---

### Post by RomeReactor on 2007-10-09
You could restart it by opening the System Monitor, finding "gnome-panel", right-click on it and select "Kill Process".

---

### Post by Shazaam on 2007-10-09
Thank you.

---

### Post by RomeReactor on 2007-10-09
For me, that's a great way to make newly installed applications show up in the menus when they initially don't, without closing my already open programs; just bear in mind that **any** application that has an tray icon is likely to get nuked in the process. You can either disable the tray icon in the programs preferences, or close the program altogether. After restarting the panels you probably won't see the Network Manager tray applet, so just press ALT+F2 and enter:
```
nm-applet --sm-disable
```
to get it running again.

---

