---
title: "Sorry If this is repost, .deb package installer"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Draken2910 on 2008-01-21
i need a 100% walkthrough on how to install .deb files. this is new so obviously for me it is frustrating. I have questions like what is a good package installer how do i open it or make it run i need everything. I use FLUXBUNTU and their forums suck i think no offense to anyone that like them. I havent even been able to login yet because the admin has to activate it. Well whatever you guys are my only hope. Thanks

---

### Post by emarkd on 2008-01-21
You can install a .deb from the GUI by just double-clicking on it.  From the command line, you'd run

```
sudo dpkg -i whatever.deb
```

---

### Post by Draken2910 on 2008-01-21
okay i did that now its saying Setting up ¨whatever.deb¨ where is it setting up at and how can i get to it

---

### Post by emarkd on 2008-01-21
If there are no errors, your software is now installed.  If the package (.deb) contained a menu item, you'll find it automatically on the menu.  If not, you'll need to know the command to start the application from the commandline and then add it to your menu manually.  You can edit your menus by right-clicking on them and selecting "Edit Menus"  If you need help with that, just ask.

---

### Post by Draken2910 on 2008-01-21
if you have time can you explain for future reference so i can copy it and keep it in a file.
oh yes and perhapes if you a good at fluxbuntu is it necessary to restart your computer after a install because it said that it completed it just doesn show up

---

### Post by bodhi.zazen on 2008-01-21
FYI: You can not double click on the *.deb in Fluxbuntu as Fluxbuntu does not have gdebi by default.

Second, what are you trying to install ? Are you sure it is Ubuntu compatible ? Why not :

sudo apt-get install <package> ???

Third, if you run into dependency problems you will need to :

sudo apt-get install -f && sudo dpkg -i *.deb

---

### Post by overdrank on 2008-01-21
> **Draken2910 said:**
> if you have time can you explain for future reference so i can copy it and keep it in a file.
oh yes and perhapes if you a good at fluxbuntu is it necessary to restart your computer after a install because it said that it completed it just doesn show up

HI an I only used fluxbox for a short time but maybe this link can help
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

---

### Post by emarkd on 2008-01-21
Sure.  If your new software did not include a menu item but you want to add one:

1.  Make sure you know the command to launch your software from the command line.  You may have to search the publisher's webpage or just go the command line and take a guess.  If all else fails, you can try a few other things:
     - If you're working from the GUI, double-click the .deb to open it in the package installer.  You may get a message about it already being installed.  Click on the "Included Files" tab and look to see what the package is going to install in the /usr/bin or /usr/local/bin directories.  This may give you a clue as to which commands you can try.
    - You can get the same information from the command line by typing dpkg-deb --contents whatever.deb

2.  Next, launch the menu editor by right-clicking on the menus and selecting "Edit Menus"

3.  Select the Menu you want to edit from the list on the left.  The right-hand pane will now display all of the items in the menu you've selected.  You can enable/disable existing menu items with the little checkbox next to each entry.

4.  To add a new entry, click the "New Item" button on the right.  In the dialog box that pops up, enter the name of the program in the "Name" box.  This is the text that will show on the menu.  Enter the command from the command line in the "Command" box.  Click OK and you're done!

Hope this helps.

---

### Post by bodhi.zazen on 2008-01-21
> **emarkd said:**
> If there are no errors, your software is now installed.  If the package (.deb) contained a menu item, you'll find it automatically on the menu.  If not, you'll need to know the command to start the application from the commandline and then add it to your menu manually.  You can edit your menus by right-clicking on them and selecting "Edit Menus"  If you need help with that, just ask.

Not in Fluxbuntu.

> **Draken2910 said:**
> if you have time can you explain for future reference so i can copy it and keep it in a file.
oh yes and perhapes if you a good at fluxbuntu is it necessary to restart your computer after a install because it said that it completed it just doesn show up

What deb was it ? not every application is graphical.

Easiest way is to log off and back on. Otherwise, in Fluxbuntu, you can :

sudo update-menus

then restart fulxbox (from the menu).

These links may also help you : 

[http://community.fluxbuntu.org/index.php?topic=424.0](http://community.fluxbuntu.org/index.php?topic=424.0)

[http://community.fluxbuntu.org/index.php?topic=36.0](http://community.fluxbuntu.org/index.php?topic=36.0)

---

### Post by emarkd on 2008-01-21
Missed the part about you running Fluxbox.  That's a pretty important distinction.  Sorry if some of my advice misled you.  I haven't used Fluxbox in years so I'll step out now and let some more knowledgeable people take over...

---

