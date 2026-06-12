---
title: "EXE files"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by don824chan on 2005-09-11
This really seems like a stupid question to me, but I can't figure out how to install .exe files (the one I'm trying to do is Civilization).  I'm thinking it might just be that it won't install on Ubuntu, but I want to make sure.  When I try to run it I get an error message that says it can't display it.  Is there an exe installation file on Ubuntu?

---

### Post by krusbjorn on 2005-09-11
You cant use exe-files in Linux (unless you are using a Windows "emulator", which i guess you arent.)

I cant use programs made for Windows at all. Welcome to the world of open source ;)

---

### Post by dave9191 on 2005-09-11
.exe files are windows execuatbles and don't work on linux. If you want to try and run them you will have to install a windows emulator like wine. 

sudo apt-get install wine

and then wine you_exe_file_name

Dave

---

### Post by don824chan on 2005-09-11
> sudo apt-get install wine

and then wine you_exe_file_name
Ok, I'm completely new to Unix/Linux/Ubuntu.  Could you please explain that part?

---

### Post by krusbjorn on 2005-09-11
Open a terminal (alt+F2 and type "gnome-terminal"). In the console that pops up, type "sudo apt-get install wine". When the installation is done, you can run exe files from the terminal by typing "wine file.exe".

However, dont expect to be able to run windows programs. For example, installing and running Civilization on a linux box probably takes *a lot* of tweaking, if at all possible.

---

### Post by dave9191 on 2005-09-11
And if you are after playing civ, there is always freeciv :)

Dave

---

### Post by don824chan on 2005-09-11
XXXX@ubuntu:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

What do I do about this?

---

### Post by dave9191 on 2005-09-11
You havent added the extra repositories, so it doesnt know where to get the package from. Find out how to add extra repositories at ubuntuguide.org

Dave

---

### Post by aysiu on 2005-09-11
Here's the link:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by tonysathre on 2005-09-12
to enable the extra repos open a terminal and type sudo gedit /etc/apt/sources.list and hit enter.  remove the # sign before all the lines with "deb" after the # sign

---

### Post by GreyFox503 on 2005-09-12
Playing windows games in linux is unfortunately hard to do, especially if you're new.  However, simple windows programs or little VB demos work fine in wine for me.

These guys are right.  If you have an .exe that's supposed to install something, then you've got the Windows version.  Try finding the website or searching Synaptic for a linux-friendly version.  If there is none, you either have to find an alternative (of which there are usually bounds) or try to emulate using Wine/Cedega.

Wine/Cedega is usually my last choice, because that involves the most work (most of the time)

---

### Post by tonysathre on 2005-09-13
i havent got anything to work with wine and havent tried cedega. i have heard that getting things to work with them takes a lot of tweaking, but what do u actually tweak to get things to work?

---

### Post by dave9191 on 2005-09-13
I installed wine becuase I though that windows programs would be a must for me when I switched. And the only thing I could think of to install to test wine was winzip. And that worked like a charm :) 

Dave

---

