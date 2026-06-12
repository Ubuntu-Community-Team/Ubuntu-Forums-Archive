---
title: "wine issues"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by namich on 2007-04-12
Hey everyone,

I need some help from all the Linux gurus out there.

I installed wine on both my PC and Laptop.The thing is when wine was installed on my PC, the installation immediately placed a link in the application menu so that I could see and start any program that was installed with wine emulator. That works perfectly.

On my Laptop is another story. Wine is definitely installed, but there is no link in the application menu. 

My question is : how can I configure my laptop to display the wine emulator start-up link when I click  applications on my screen.I am using the Gnome environment.

I installed office 2003 using Wine emulator, on my laptop,and I have no idea how to start the application.

Thanks all.

---

### Post by forrestcupp on 2007-04-13
Try this and see if it works.

Go to System->Preferences->Main Menu.  This will open up a window where you can manually edit your menus.  Look under the Applications menu tree on the left side, and see if there is an entry for wine.  If there is, click on it.  On the right side you should see an entry called Program Files.  If the box isn't checked, check it.  You may also have to check the individual things within the Program Files menu.

If there isn't an entry called wine, I don't know what to tell you, other than that you can use this to manually put things in the menu.  You can make a new entry, name it, and in the command box you will have to type:
```
wine /path/to/program/programname.exe
```
The way you find things installed in wine is by going to the .wine directory in your home directory.  If you are using nautilus, you have to press ctrl+H to show the hidden files.  Within the .wine directory is a sub-directory called drive_c and in that is one called Program Files.  You should find your installed programs there.

Edit:
I'm interested to see if Office 2003 works with wine.

---

