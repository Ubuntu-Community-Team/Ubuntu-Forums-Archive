---
title: "&quot;Ghost&quot; Kubuntu-Desktop ??"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by ubromtoo on 2007-07-16
I'm running Dapper 6.06 with the default Ubuntu desktop.

Have installed and then uninstalled kubuntu-desktop three

times because of a problem which turned out to be easily 

solved by renaming /home/username/.kde 
 
  to 

                   /home/username.kde_bad  
 
and then letting the system reconstruct a new(undamaged) 

folder.

   but, i didn't know that at the time, hence all the 

newbie installing-and-uninstalling.

   Anyway, now there is only one problem remaining :

the Users & Groups won't open for me :

    the notice says its probably caused by an orphaned module.

     Not knowing what else to do, I uninstalled kubuntu-desktop

and ran a search for all files with "kde" in the name, hoping

to find and delete the "orphaned" module. the search turned up

over 600 files !!  Is there somehow a hidden kubuntu-desktop

installed but not reachable ? I'm afraid to delete all those

files !!  

     I've been running a few kde apps since long before

installing the kubuntu-desktop, but not 600 apps !!

---

### Post by Al3xK3aton on 2007-07-17
Why did you hit return in the middle of every line?

If you uninstalled KDE and it's still there, you should try reformatting if you really want to remove all traces.

---

### Post by ubromtoo on 2007-07-17
A13xK3aton :

  1) I pasted from a sticky-note ; my bad.

  2) Reformatting ?  forgive my ignorance, but how do I do that ?  Grateful for advice

---

### Post by gunksta on 2007-07-17
I assume you are trying to use Ubuntu's Users and Group dialog.

Open Synaptic. Search for gnome-system-tools. Right click on it and mark it for re-installation. You can also right click on it and install anything that is recommended or suggested. I would also reinstall ubuntu-desktop. My guess? You accidentally deleted something important when you were trying to delete KDE. In fact, I would not be surprised if ubuntu-desktop has already been removed from your system. Don't sweat it, just re-install it and everything will be peachy keen.

As for removing KDE, that's a little tricky. First, if you really want to eliminate something, don't remove it, PURGE it. When you right click on a package in Synaptic, you should see the option to Purge the package. Choose this. Sometimes, because of dependencies, you will remove more than you think, so before you actually let the computer get to work go to Custom Filters -> Marked Changes and make sure everything is set to purge, not remove.

As for killing off the rest of KDE, it's remarkably easy. KDE is built on a toolkit called QT (pronounced Cute). Search to qt with synaptic. If you have anything with qt in it, Purge it. This will automatically also remove almost everything related to KDE. You can later go back and search for KDE and make sure you didn't miss anything. Some of the doc packages have poorly written dependencies and will be left behind.

You can also manually look at your system with Synaptic -> Status -> Installed. This is a list of EVERYTHING installed on your system. If you would like to find orphaned packages (so you can delete them) install deborphan. It is a command line tool that is easy to use. After installing it, open a terminal (gnome-terminal in your case) and read the man page.

man deborphan

I hope this rambling reply helps.

---

### Post by rickycodie on 2007-07-17
try this command

sudo apt-get autoremove --purge kde-desktop

that's what worked for me.

---

