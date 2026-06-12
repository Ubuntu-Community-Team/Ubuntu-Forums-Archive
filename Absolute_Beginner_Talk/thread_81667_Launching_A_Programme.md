---
title: "Launching A Programme ??"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by CyiPherX on 2005-10-24
OK, most likely a simple answer for this but....i have installed a programme from the package manager, i can launch it from the terminal window, but their is no icon on the GNOME applications menu for it.

So how do i go about putting an icon on their to launch it, and second question , in windows xp during installation of a programme it always asks where you want to install it to, so in linux if you wanted to look at the folder or files related to an application , where abouts in the file browser do you navigate to , to look at those files??

CyiPherX:confused:

---

### Post by Beggar on 2005-10-24
Alright, to add an application icon to the gnome menu, right click on the menu and choose 'Edit Menus'. Now just choose the location where you want to add the icon from the menu, and press 'new entry'.  Now just fill in the information you want (name, description, the command which launches the program from the terminal, and choose your icon).

---

### Post by cstudent on 2005-10-24
To find where and what files are installed with a package here is a little trick I use. I open Synaptic and find the package. Click on the tab for installed files. If the tab isn't showing then check your preferences.

If you didn't get a menu item added then it may be a couple of things. First try logging out and back in. Another possibility may be it's a terminal app or KDE app. If you go to the Unofficial Ubuntu Guide ([www.ubuntuguide.org](www.ubuntuguide.org)) you will find several examples of where the author created a desktop file to create a menu item. You can use these to guide you in making a menu item for your program.


Bill

---

### Post by brentoboy on 2005-10-24
in many cases, you can run a new program simply by typing its name in as a new command:

Applications (menu) > Accessories > Terminal

then at the terminal prompt, type the name of the program, and cross your fingers.

if it works, skip to the part below about making a launcher for it.

if it didnt, you need to decide where it is.
if it is a game, it is probably in /usr/games look in there and see if any of the files in there look like they are the new game you installed.

once you find it, double click it and see if it runs what you expect.
if it works, skip to the part below about making a launcher for it.

if it is an application (instead of a game) it is probably in /usr/bin (that is where binary executable files are stored that are expected to be used by "normal" users -as opposed to root).

the trouble is, all your binaries are in there, and there isnt a folder for each installed program group. if you find it great, if not, then ask synaptic where it put the files..

open synaptic
System (menu) > Administration > Synaptic Package Manager
find the new package in the list I'll use bluefish as an example.
once you select it, there are details about the package. (actually, you probably have to tell it you want full details in the preferences part of synaptic) Settings > Preferences > "Show package properties in the main window"

now, the package description area (below the package list) shows more than just the description of the selected package, it has a few tabs.  One of which is the "installed files"  this tells you everything that was added by the installer. (folders, files - everything)  find the one that looks like a program (in the case of bluefish its: /usr/bin/bluefish)

run that from the command line in the terminal.

---
now make a launcher.

right click the desktop
fill in all the details with whatever you like, but in the command field put the name of the binary that you found.
when you are done, click ok and then test it out.

---

now, you ask the question, why did they install it to such a "god awful" cryptic place?!!!

so, look at it from this perspective: allowing you to put stuff whereever you want is an organization flaw, and the end result would be that we wouldnt be able to help you as easily.

Unix (and therefore linux) organizes files and folder structure based on what kind of files they are, not based on which files are related to each other.  All the executalbe files are together, all the configuration files are together, all the icons are together. it makes life easier - once you know where those folders are, and it makes it easy to backup your config - just backup the /etc folder - you get all the config files and nothing else.

---

### Post by CyiPherX on 2005-10-25
Thanks everyone for those answers, all setup and working:)

---

### Post by mfyahya on 2005-10-28
Thanks brentoboy, your post really helped me a lot.
I have one question though, I noticed that the command field for many of the apps in the gnome menu have stuff like %f %u etc after the executable name. What are these?

---

### Post by mfyahya on 2005-10-28
dupe - sorry

---

