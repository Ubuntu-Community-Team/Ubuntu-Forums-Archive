---
title: "Debian package of Avast activation"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2006-12-28
Ok, just downloaded the latest version of Avast for linux and used the Debian package installer and all went well. Now what? Where do I go or what do I do to intitiate the program?? Thanks for help in advance.

---

### Post by deadgobby on 2006-12-28
Open up the Terminal and type in Avast. If that does not work use avast in lower case.
Gobby

---

### Post by mikewhatever on 2006-12-28
Check here: [http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html](http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html)
I've also installed avast and it worked.

---

### Post by Matchless on 2007-01-28
Try this:

                                           [COLOR=#000000][SIZE=2]_**Howto: Install Avast free anti-virus in Kubuntu Edgy**_[/SIZE][/COLOR]  
Download the avast4workstation_1.0.7-2_i386.deb file from the free downloads on the Avast website and save it on your Desktop. 
Avast requires you to get a free registration number, so while you are on the website, click on register, fill in your email address and personal details and a registration number will be mailed to you. You need this to register when you do the first time running of the program.  
Now right click on the avast4workstation_1.0.7-2_i386.deb file and select Kubuntu Package Menu, Install package  
Thats it! 
Now create a menu item by right clicking on the menu Under Utilities create a menu item called Avast anti-virus
In Command enter avastgui and set Advanced Options - run as different user - root 
Select and Icon /usr/lib/avast4workstation/share/avast/icons/avast-appicon.png  and Save 
Run from menu and enter the registration number emailed to you. 
Run the program and do an update while on line.  
The gui looks very ugly and you can make it look like kubuntu: Go to /usr/lib/avast4workstation find folders lib-gtk2 and lib-x11 Delete both folders Now you have a nice looking gui!

---

