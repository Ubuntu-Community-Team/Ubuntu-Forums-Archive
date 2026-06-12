---
title: "Installed Opera... now where is it?"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by drdeutsch on 2005-06-18
Hi there.  Started using Ubuntu a few hours ago... this is my first time working with Linux, and I thought I would just "take the plunge," so to speak.  Anyway, I've managed to install it and get my network configured properly.  But, I prefer Opera to Firefox, so I managed to download it to my /home directory and install it with the "sudo dpkg -i" command, which gave me this:

> Selecting previously deselected package opera-static.
(Reading database ... 58139 files and directories currently installed.)
Unpacking opera-static (from opera-static_8.01-20050615.1-qt_en_i386.deb) ...
Setting up opera-static (8.01-20050615.1) ... 

and then it went back to my terminal prompt. So.... now how do I use Opera and how would I go about making a Desktop shortcut to it?

Any help for this total Noob is appreciated!
Thanks,
drdeutsch

---

### Post by Xian on 2005-06-18
[QUOTE=drdeutsch]So.... now how do I use Opera and how would I go about making a Desktop shortcut to it?[/QUOTE]
Right-click on the desktop and choose "Open Terminal"
At the prompt enter the program name:

```
$ opera
```
To create a shortcut, again right-click on the desktop and this time choose, "Create Launcher" Then just fill in the appropriate information, being sure to place the word 'opera' where it asks for the command. The rest you can fill in with whatever you desire. Then select an icon and click 'Okay'.

---

### Post by drdeutsch on 2005-06-18
Thanks.

I'm sure I'll be back with many more questions before I get the hang of this.

drdeutsch

---

### Post by Vicsun on 2005-06-18
[QUOTE=Xian]Right-click on the desktop and choose "Open Terminal"
At the prompt enter the program name:

```
$ opera
```
To create a shortcut, again right-click on the desktop and this time choose, "Create Launcher" Then just fill in the appropriate information, being sure to place the word 'opera' where it asks for the command. The rest you can fill in with whatever you desire. Then select an icon and click 'Okay'.[/QUOTE]
I know I didn't post the the thread, but I'd still like to chip in with a question...

Why does just typing *opera* in the terminal work? When you launch the terminal you find yourself in the /home directory. Is the *opera* executable (or a shortcut to it) placed in /home, or typing opera in a newly opened terminal equivalent to **start->run->explorer** in windows? If that's the case (the latter), is there a more... straightforward way of launching an application? How would I know what to type in the console to launch a newly installed program?

---

### Post by Xian on 2005-06-18
[QUOTE=Vicsun]If that's the case (the latter), is there a more... straightforward way of launching an application? How would I know what to type in the console to launch a newly installed program?[/QUOTE]
From the main panel choose one of the headings and find the "Debian Menu" title. Bring your mouse along and then goto the Apps > Net column. You should see Opera listed in that set of programs.

I find it easier to just create a launcher on either the desktop or main panel and use that to start the program. Starting it from the command line is helpful when assisting others with potential problems because if Opera crashes there will be some error messages that appear in the terminal explaining the cause of the fault.

---

### Post by desdinova on 2005-06-18
[QUOTE=Vicsun]I know I didn't post the the thread, but I'd still like to chip in with a question...

Why does just typing *opera* in the terminal work? When you launch the terminal you find yourself in the /home directory. Is the *opera* executable (or a shortcut to it) placed in /home, or typing opera in a newly opened terminal equivalent to **start->run->explorer** in windows? If that's the case (the latter), is there a more... straightforward way of launching an application? How would I know what to type in the console to launch a newly installed program?[/QUOTE]

Typing "opera" in the console works as there are particular directories Linus searches first for apps - to get the Equivalent of Start -> un you can either ALT-F2 or from the Applications Menu select Run Application

A lot of software will place itself in the Menu's for you, and the Ubuntu Guide talks about how to do it for those that don't

---

### Post by dakira on 2005-07-04
[QUOTE=Vicsun]I know I didn't post the the thread, but I'd still like to chip in with a question...

Why does just typing *opera* in the terminal work? When you launch the terminal you find yourself in the /home directory. Is the *opera* executable (or a shortcut to it) placed in /home, or typing opera in a newly opened terminal equivalent to **start->run->explorer** in windows? If that's the case (the latter), is there a more... straightforward way of launching an application? How would I know what to type in the console to launch a newly installed program?[/QUOTE]

Hi,

When you use the terminal to start an application Linux will (unlike Windows) ONLY run programs which are in the PATH (same as windows PATH). During installation Opera copies its executable to /usr/bin (which is in the PATH). Other programs just create a link inside /usr/bin which links to the real location of the executable.

For everything not in the PATH you will have to specify the complete location of the file you want to run. Even if it is in the current directory. That's why you have to run files in the current directory with ./mybinary.

Hope that helps
dakira

---

### Post by ceti on 2005-07-05
[QUOTE=Vicsun]I know I didn't post the the thread, but I'd still like to chip in with a question...
 
Why does just typing *opera* in the terminal work? When you launch the terminal you find yourself in the /home directory. Is the *opera* executable (or a shortcut to it) placed in /home, or typing opera in a newly opened terminal equivalent to **start->run->explorer** in windows? If that's the case (the latter), is there a more... straightforward way of launching an application? How would I know what to type in the console to launch a newly installed program?[/QUOTE]
 
To place items directly in the menu trees, install SMEG from Synaptic. Open it, choose a menu (ex: Internet), fill the first field with Opera, the third with the complete path. Where's the path? --> well, open a terminal and type "whereis opera" (no quotes). You'll get some results. Usually, the first one is the path (something like /usr/bin/opera or /usr/local/opera etc). Copy & paste it the usual way in that field. Then click on NO ICON and select the Opera icon from /usr/share/pixmates or /usr/share/icons (or even open Nautillus, click on Shown Hidden Files from the View menu, click on .local/share/apps). Click Ok and yoy're done.
SMEG is a program developed by a unbuntuer and gives you the power to include/exclude/edit everything you want from the Applications menu.
Hope this helps.
(Another way to discover where are executables & icons: open a terminal, type **sudo updatedb**, hit ENTER and wait. When the database is updated, type **locate opera** (to view every archive opera-related) and/or locate opera.png or opera.ico or opera.xml (to find the icon).
I'm on my job now, sorry if I quoted something wrong.
 
cheers

---

### Post by dakira on 2005-07-05
[QUOTE=ceti][...]Where's the path? --> well, open a terminal and type "whereis opera" (no quotes). You'll get some results. Usually, the first one is the path (something like /usr/bin/opera or /usr/local/opera etc). Copy & paste it the usual [/QUOTE]
My I correct you? You should use "which opera". This gives the exactly the executable which is the one you start when you just type "opera" in a terminal.

cheers
dakira

---

### Post by ceti on 2005-07-05
[QUOTE=dakira]My I correct you? You should use "which opera". This gives the exactly the executable which is the one you start when you just type "opera" in a terminal.

cheers
dakira[/QUOTE]

well done.
I told you, I was working, i could feel my boss' breath behind my back :)

---

