---
title: "Finding installed softwares"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by bluntu on 2006-08-18
In Windows you install a software and it goes right into the start menu and if it doesn't you can find it in c:\program files

In Ubuntu, it goes to the "Applications" Menu but sometimes it doesn't so how do I refresh it to see it? And what if it doesn't go to the menu, where do I find it?

Is there a location in Ubuntu that all software installed to? Like C:\program files for Windows.

---

### Post by Klaidas on 2006-08-18
Software is ussually stored to /usr
To find it if it's not listed, > whereis program

---

### Post by givré on 2006-08-18
In linux, you could first try by the terminal.
Open a terminal, put the first letter of your app and press TAB to see all the executable beginning by those letter, your app should be there.
Specificaly in ubuntu, to know what file install a package, go to synaptic, search for the package right-click > setting, and it should be in the install files tab. The executable (what you are searching for ) are usually in a /bin direcory (/bin, /sbin, /usr/bin, /usr/sbin...)

---

### Post by ciscosurfer on 2006-08-18
There are many ways to search for files.  And some programs that aren't "menu aware" will not install themselves to your Applications menu.  You can install "menu" (enable universe repository) that will show you all "menu aware" items installed on your computer.  It stands for "Debian menu" and I find it helpful if I don't want to trudge through my terminal to find a particular app.```
sudo aptitude install menu
```

In a terminal, however, you can issue many commands to find your program; choose any of the following:```
sudo updatedb    ## updates your database..may take a minute or two
locate *program_name     *## issue this after updatedb completes

find / [I]program_name

[/I]which [I]program_name

[/I]whereis *program_name*
```

---

### Post by muep on 2006-08-18
In linux systems, most of the executable files ( they are like .exes in windows, but don't have the .exe suffix) are collected in a few special directories. A lot of them are in /usr/bin and /bin, but there are others. You can check which ones are currently used with the command:

echo $PATH

You usually don't need to care about where the executable files are. You can start the programs by typing their names in the Terminal, or you can press alt+f2 and then give the program's name. For example, Firefox can be started with the command:

firefox

You can also only write the beginning of the program's name and press Tab to autocomplete the name. If there are multiple programs names starting in a similar way, press Tab again to see a list of them.

It is easy once you learn it :)

---

### Post by ciscosurfer on 2006-08-18
> **givré said:**
> In linux, you could first try by the terminal.
Open a terminal, put the first letter of your app and press TAB to see all the executable beginning by those letter, your app should be there...

I think you mean TAB-TAB (for Bash command completion) ;)

---

### Post by ciscosurfer on 2006-08-18
> **muep said:**
> ...You can also only write the beginning of the program's name
At least a few letters

> and press Tab to autocomplete the name. If there are multiple programs names starting in a similar way, press Tab again to see a list of them...This makes the best sense overall in terms of command-line completion.

---

### Post by givré on 2006-08-18
> **ciscosurfer said:**
> At least a few letters
 
This makes the best sense overall in terms of command-line completion.
Ok, my explaination wasn't really clear. :cool:
But auto-completation is easily self-understable from the moment we press the TAB key

---

### Post by ciscosurfer on 2006-08-18
> **givré said:**
> Ok, my explaination wasn't really clear. :cool:
It was clear to me, givré :D

---

### Post by cjm5229 on 2006-08-18
Type ```
killall gnome-panel 
``` into terminal. That will refresh the panel. Type the name of the App that you are looking for into the terminal and see if that starts the program, if it does,  use Alacart  Menu Editor  to create a shortcut  use the command that you used to start the app in terminal as the "command" If that doesn't work use synaptic, search for the app, then use "properties" to find the folder that contains your bin file. Click the bin file to see if that starts the App. if it does then drag and drop it to The "command" box in Alacarte and create your shortcut.

Edit; Gosh, I type slow! :oops::D

---

