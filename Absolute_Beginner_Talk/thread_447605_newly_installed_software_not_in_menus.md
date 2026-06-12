---
title: "newly installed software not in menus"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-18
Why do some newly-installed software packages not show up in the applications menu, even if installed through the synaptic thingie and from the repositories? I just installed lyx and it doesn't show up, whereas audacity did.

---

### Post by klytu on 2007-05-18
> **ginestre said:**
> Why do some newly-installed software packages not show up in the applications menu, even if installed through the synaptic thingie and from the repositories? I just installed lyx and it doesn't show up, whereas audacity did.

Good question! I haven't been able to figure out why this is the case with the default menu ever since I have been using Ubuntu. However, if you install the Debian menu structure: ```
sudo aptitude install menu-xdg menu

``` The Debian menu will appear as a sub-menu of the default menu and it will contain launchers for just about every application you install.

---

### Post by Jussi Kukkonen on 2007-05-18
That would be a bug in the packaging (if the package contains a GUI application, like Lyx) or intended behaviour (if the main component of the package is not graphical).

Do file a bug on Lyx if it didn't get an icon.

---

### Post by derred on 2007-05-18
You have a better chance of seeing all your software if you use the debian menu(I usually activate it with automatix). I think that it's a problem with the packages themselves. You can add applications by right clicking the Applications button and clicking edit menus.

---

### Post by 3rdalbum on 2007-05-18
Or, you could go into Synaptic and find the package that you installed. Right-click on it and select "Properties". Go to the "Installed Files" tab, and it will give you a list of all the locations of files for the package. Any of the files in /bin, /usr/bin or /usr/local/bin will be programs that you can run by running the name as a command.

For instance, if you have Abiword installed (it does show up in the menu anyway):

Installed Files:
...
/usr/bin/abiword
...

So you could create a launcher or a menu item with the command "abiword".

---

### Post by akudewan on 2007-05-18
Lyx shows up in the KDE menu under "Office". I have lyx, lyx-qt and lyx-common installed.

I don't know about Gnome though...

---

### Post by ginestre on 2007-05-18
> **akudewan said:**
> Lyx shows up in the KDE menu under "Office". I have lyx, lyx-qt and lyx-common installed.

I don't know about Gnome though...

Yes, that's where I was expecting it. But when I right clicked on the apps menu,  as suggested, and went to look I found Lyx was already checked as though it was already appearing inthe menu, which of course it isn't. Does it maybe have to re-start to take effect? I'd sort of got out of the habit of having to restart to have changes take effect...

---

### Post by tei on 2007-05-18
check this dir /usr/share/applications/
look for something like lyx.desktop

and look for line Categories=...
this line is the place where this program is (i'm not sure about this, sorry if it wrong ==")

i don't install this program, so i don't know what this line will be
may be u should look this line in another file that exist in menu

ps. sorry for my poor eng :confused:

---

### Post by ginestre on 2007-05-19
Thanks to everyone for the input.  It turns out that Lyx turns up of its own accord in the right place    on the apps menu next time you boot the PC, and I hadn't for a few days....

---

