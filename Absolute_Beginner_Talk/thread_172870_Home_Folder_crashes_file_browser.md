---
title: "Home Folder crashes file browser"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by cowley on 2006-05-09
Hi - i am a newbee to all that is linux, i have the ubuntu depper drake latest beta version:  The problem i get is if i try to browse my home folder the file browser locks up, i have to force it too quit, and then it opens up again and locks up.  i cant even shut down or reboot so have to turn the laptop off on the switch.  i can browse all the other folders fine. 

thanks for any advice

simon

---

### Post by trent dillman on 2006-05-09
...

---

### Post by Monster_user on 2006-05-09
[QUOTE=trent dillman] Try (with the command line or another file browser) [/QUOTE]

Translation,...

Open a terminal, and then **type 'ls ~'** (LS in lower case, the tilde '~' points to your home folder).

Right-click to copy, and paste the results. You may want to post them here. If it does not return a lot of results, then try  'ls -a ~', to list "Hidden" files.

Also, try install another file manager, using "Synaptic". There are several to choose from. 

You can install **Konqueror** the file manger used by KDE/Kubuntu. I warn you, the Kubuntu desktop is a big download. Installing Konqueror may require you to download 300mb, and may require almost a gig of free space. Dapper uses Gnome, and therefore the **Nautilus** file manager by default. *(rambling,... Windows uses "Explorer.exe" a.k.a "Windows Explorer", and the Mac uses the "Finder".)*

Other lighter, smaller choices include,...

xfm = A light, quick download. It is also a VERY basic file manager, and is ugly.
xffm4 = Is an XFCE file manager, and would look good on Xubuntu.
thunar = Is also an XFCE/Xubuntu file manager.

gnome-crusader = Is a file manager for Gnome, and fits in with the default Dapper install. It was designed to be a more powerfull file manger.

krusader = Is a popular KDE alternative to Gnome-Crusader. Unfortunately, it may require KDE, which takes a while to download. It is the most popular desktop in Linux. Kubuntu, Suse, Xandros, Mepis,...

Midnight Commander, or **'mc'** = is a console file manager, that may seem like the old "DOS Shell" (dosshell). Except this is more powerfull by far.

I recommend trying xffm4, or thunar.

---

### Post by cowley on 2006-05-09
hi thanks guys

i only had 4 files in the home folder (!), 2 of which were image folders (desktops) which i removed via terminal rm command.  y would this cause this problem? i have set up a 'my documents' style folder structure now accessable from the desktop which i will use to store images, music etc.  am i likely to run into similar problems there too? will i have the same sort of problem with another browser such as xffm4 or thunder?

thanks

simon

---

### Post by Monster_user on 2006-05-09
[QUOTE=cowley] i have set up a 'my documents' style folder structure now accessable from the desktop which i will use to store images, music etc.  am i likely to run into similar problems there too?[/quote]
Probably. Nautilus does not use individual folder settings often. They are not on by default. So it is likely a problem with your Nautilus settings.

Open Nautilus, or your home folder. Then select "Preferences" from the Edit Menu, and go to the "Preview" tab. 

Nautilus -> Edit -> Preferences -> Preview

In the second section, the second, and third drop down box. Try setting previews to "Never", or drop the file size from 5mb, to 500kb. Especially if you have 256mb of RAM, or less.

 [QUOTE=cowley]will i have the same sort of problem with another browser such as xffm4 or thunder?[/QUOTE]
Nope, I seriously doubt it.

Unless there is something seriously wrong with your system, then the other file managers will work fine.

---

### Post by cowley on 2006-05-09
hi again!

i have downloaded/installed xffm4 via synaptic, do i need to remove the default file browser? and how do i start the new one? thanks!!!

simon

---

### Post by Monster_user on 2006-05-09
Nautilus not only is the File Manager, but also your desktop. With the icons, and the wallpaper. I don't recommend that you remove it.

XFFM4 should be in the Applications Menu, under "System Tools". 

If it is not there, then you will have to run it from a terminal. 

Applications -> Accessories -> Terminal -> xffm4

Just to make sure that is the right command, then add it to the Menu Bar. Right-click the panel, and select "Add to Panel". Then click on the **"Custom Application Launcher"** Button, at the top of the add box.

Type **XFFM4**, and then select the "command" box, and type 'xffm4'. Then click on the "No Icon" button, and select a File Manager icon, or one you will recognize. Then you can just click on it, whenever you need to browse a folder with images.

---

### Post by AiBo on 2006-08-02
I have a similar problem with nautilus' file browser.  Mine is fine until I go about 2 or 3 deep into a folder set.  For example:

from the desktop select AAAA folder---> then select BBBB folder ---> then try to open CCCC folder which results in a lock up and eventually having to force quit the browser.

I just did a fresh install of Dapper, hoping that it might clean up the problem.  No luck.

I tried reducing the preview size.  Also with no luck.

I do not mind using another file browser, but this seems like it might be a  bug I would want to address...

Thanks for any help you all might be able to offer!

---

### Post by genevieve on 2007-07-05
I had this exact problem right after I had installed a new piece of software. I moved the new software folder out of my home directory and it solved the problem.

BTW you can get out of the forced quit/repeat loop without the hard reboot by restarting X (ctrl-alt-backspace). Also strangely by opening the file browser on something else, like the desktop, which won't appear to work, but then when you do the forced quit on the crashed file browser it restarts on the desktop and doesn't crash.

---

### Post by venom9122 on 2007-07-23
THANK YOU MONSTER_USER, you just saved me with that comment, wow, that fixed it, if only i could have found out how to fix my libpng12 error this easily....

---

