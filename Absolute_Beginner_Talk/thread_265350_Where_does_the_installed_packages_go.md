---
title: "Where does the installed packages go ??"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-09-25
Hi everyone...

Jus installed my Ubuntu 6.06 LTS ,2 weeks ago and i have been downloading applications and installing them.(linux is great , all of them for free:-D  ) 

Mainly after you install some packages they apear in Ubuntu menu, however i got some apps that they dun apear anywhere.? and i was wondering ,i jus installed them, where did they go ? tried searching the folders for them, but i ended up getting more confused:-? .

and one more thing, how do you run the program within the terminal , i mean what is the code, or set of procedures.

and i was also wondering how to create lunchers , codes for that also will be appericated .thanks :rolleyes:

---

### Post by Sarisar on 2006-09-25
Where they appear depends on what program (unfortunately).  One thing I found to be VERY helpful is to go into synaptic package manager and right click on the package.  It has a list of installed files which may help.

Also sometimes the menu item IS there... but the menu hasn't refreshed.  Right click on the menu and 'edit menus' to see.  If not you can add in a new command there.

With regards to running a program in the terminal, you just type it's name basically.  So if you want to run nautilus, you just type nautilus.  Well actually that isn't just it.. there is more to it then that, but for now that will do you (just don't close the console window down!)

That should get you going for now though :)

---

### Post by TLE on 2006-09-25
> **lifemaximum said:**
> Hi everyone...

Jus installed my Ubuntu 6.06 LTS ,2 weeks ago and i have been downloading applications and installing them.(linux is great , all of them for free:-D  ) 

Mainly after you install some packages they apear in Ubuntu menu, however i got some apps that they dun apear anywhere.? and i was wondering ,i jus installed them, where did they go ? tried searching the folders for them, but i ended up getting more confused:-? .

and one more thing, how do you run the program within the terminal , i mean what is the code, or set of procedures.

and i was also wondering how to create lunchers , codes for that also will be appericated .thanks :rolleyes:

Welcome !
You run programs from the terminal simply by typing their name, if you want to use the terminal for something else afterwards you follow it by a &, so to start firefox in the background of the terminal (so it doesn't lock it) simply type
```
firefox &
```
followed by enter. Also experiment with the tab key it'll finish the command you were typing if it is unique.

To find out where the executeable of a program is you can use the terminal command which, so e.g. to find out where the executeable for firefox is type:
```
which firefox
```

I'm not sure what you mean by lunchers. 

If you want to explore the commandline I would advise you to look at a tutorial, try one of these:
[http://www.linuxcommand.org/index.php]("http://www.linuxcommand.org/index.php")
[http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html]("http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html")

Regards TLE

---

### Post by maaronB on 2006-09-25
One of the wonderful posters on this site has just recently made a nice explanation of the linux filesysytem.  
Read it to find out where it all goes when you install an application.
[http://ubuntuforums.org/showthread.php?t=258611](http://ubuntuforums.org/showthread.php?t=258611)

To run packages that don't have a menu entry, just hit Alt-F2 this will bring up a run dialog.  Just type the name of the program.

---

### Post by maaronB on 2006-09-25
To create a launcher just right click on the terminal then press the button marked "Create Launcher" give it a name in the section marked Name.
And the path to the executable in the section marked Command.

For instance if I wanted to be able to play regular solitare from my desktop, I could "Create Launcher" 
Name= Solitare
Command= /usr/games/sol

An icon is nice so I would click on the button marked icon then pick one from the list.

---

### Post by lifemaximum on 2006-09-26
Thanks everyone... I really learned alot .. specially thanks for the link to the file system...now i get i:cool: t.

---

