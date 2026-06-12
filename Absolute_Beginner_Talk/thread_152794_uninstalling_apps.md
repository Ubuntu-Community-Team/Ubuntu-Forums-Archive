---
title: "uninstalling apps"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by moon_dog on 2006-03-30
how do you uninstall apps? do you just delete the folders?  or is there some kind of uninstall manager?

---

### Post by WoodyMahan on 2006-03-30
Go to Synaptic   System-Administration-Synaptic Package Manager

Search for the app that you want to uninstall.  Click on the app (it should be highlighted in green) and then Click Mark for Uninstall, Click Apply.

---

### Post by nalmeth on 2006-03-30
There are a number of ways of uninstalling programs.
Deleting folder sounds like windows talk, and doing that is bad practice in windows too.
If you want a GUI use synaptic:
ALT-F2 
gksudo synaptic
look for installed programs, deselect the ones you want uninstalled, and mark the changes.

I personally prefer the terminal. If I wanted to uninstall gxine, in a terminal I would do:
sudo apt-get remove gxine

to purge its configuration files as well:
sudo apt-get --purge remove gxine

---

### Post by moon_dog on 2006-03-30
hey thanks.  how about in the shell? is ```
apt-get remove
``` the correct command?

---

### Post by nalmeth on 2006-03-30
Yep, but you have to remember "sudo" to give yourself admin priviledges.
You'll be prompted for your user password (which you set at installation)

sudo apt-get remove

---

### Post by moon_dog on 2006-03-30
how about deleting folders with files in them?  something like the old deltree command of DOS.  ```
rm 
``` only seems to work with files, and not folders.

---

### Post by nalmeth on 2006-03-30
I think that:
rm -r
will remove the folder recursively, meaning the folder and everything inside
and I think:
rm -i
should be interactive, so you may be asked whether or not you want to delete all the files inside. 
Try those.
You could just use nautilus, but I tend to like to use the terminal as well.

---

