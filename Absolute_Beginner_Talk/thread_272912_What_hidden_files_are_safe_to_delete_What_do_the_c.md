---
title: "What hidden files are safe to delete? What do the correspond to?"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-07
So how can I tell what hidden files do and are they safe to delete?

Here are some that I have.

[B].recently-used
.dmrc
.lesshst
.rnd[/B]
.adobe
[B].fonts.cache-1
.local[/B]
.ssh
[B].gconf
.thumbnails
.bash_history
.gconfd[/B]
.mozilla
.xmms
[B].cache
.gnumericrc[/B]
.mozilla-thunderbird
[B].xscreensaver
.config[/B]
.googleearth
.mplayer
.cups
[B].ICEauthority
.qt[/B]

The one's in bold are the one's that i'm really worried about since I can guest what the others are for.

Also I share a /home dir with a ubuntu server and two xubuntu machines that are setup with different apps. One other thing that bothers me is what if some of these files belog to apps i have tryed out and removed?

maybe im just too fussy about my system.

---

### Post by carloshgdv on 2006-10-07
honestly, as they are hidden, let them stay hidden. Not only could you potentially screw up your system, but could screw up your system in the future if an app needs one of those folders, so I personally suggest you let it be

---

### Post by jaboua on 2006-10-07
.recently-used: record of what files GTK apps recently have used (so you easier can load them again)
.dmrc if I rememmber correctly, what kind of window manager you chose in the login manager
.lesshst history of what the pager "less" (for example used by default when viewing manpages) has done
.local contains for example changes you made to the menu
.gconf has configuration for gnome apps
.gconfd has configuration for the gconf configuration framework
.fonts.cache is a list of where fonts can be found and such (man fc-cache)
.thumbnails should speak for itself - thumbnails of different files
.config contains configuration for some apps (look inside)
.bash_history contains a history of what shell commands you have run (run "history" or press the up arrow to get a demonstration why)
.gnumericrc should be a config file for the spreadsheet app gnumeric
.xscreensaver is probably screensaver configuration (xscreensaver is a screensaver system)
.qt contains QT configuration - QT is, just like GTK, a toolkit for building graphical applications. For example skype, kde and opera are build around QT, while gnome and firefox is around GTK (by default, I belive firefox can be compiled with other toolkits as well).

---

### Post by tommcd on 2006-10-07
I assume these files are in your home folder. The hidden files in your home folder are configuration files. e.g., .mozilla and .screensaver are self explanatory. 
Some are cache files (.recently-used, .bash_history). I would guess the cache files would be ok to delete, but they take up so little space I would not worry about it. If you really want them gone, try renaming them. If that does not cause any problems, they are likely ok to delete. I just leave them alone. They are not a security risk, if that is what you are concerned about.

---

### Post by kwalo on 2006-10-07
Within theese hidden files, or dot files all configuration of specific application is kept. You can remove any dot file, or directory, that keeps configuration of an application, that you don't use, or that you have removed. Don't remove such folders as .ssh, .update-notifier, .esd_auth, .cups (If you have a printer). Theese components are used by other applications, so their removal would be harmful.

If you removed a package foo, you can safely do```
rm -rf ~/.foo
```that won't do any harm.

---

### Post by jaboua on 2006-10-07
> **carloshgdv said:**
> honestly, as they are hidden, let them stay hidden. Not only could you potentially screw up your system, but could screw up your system in the future if an app needs one of those folders, so I personally suggest you let it be
Actually I regularly go through the hidden files and folders and delete those I don't need. If you don't use a login manager, don't delete a file named ~/.xinitrc - but otherwise, applications should create default configuration files if they don't exist. I wouldn't suggest that you wipe everything though unless you like reconfiguring stuff...

---

### Post by guysmiley25 on 2006-10-07
Thanks for the help guys! It has helped alot.

---

### Post by podunk on 2006-10-07
Everything you install through the Package manager can be uninstalled completely by searching for the name and right clicking and choosing “Mark for complete removal”

Apps that you compile and install yourself can be entered into the Package manager very easily for later complete removal by using the 
checkinstall

command instead of 
make install

Checkinstall is available through the Package manager. It enters a package in Synaptic of all the files you installed for an app. This way when the install is done you can delete the directory where you complied the app and still completely remove it later.

---

