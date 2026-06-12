---
title: "I am a Linux Newbie-I need some help"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by supportbroker on 2007-07-12
I just installed Wine (I think) I mean it shows up in the add/remove applications list and I can't figure out where it is or get it to run...I mean there is no icon on my desktop or drop down on my taskbar...Where is it? and how can I get it to run?

Help

---

### Post by tarek on 2007-07-12
If you have an Windows app, then either right click and open with and enter wine as the command or open up a terminal and go to the directory where your exe is and enter: wine something.exe

---

### Post by godd4242 on 2007-07-12
> **supportbroker said:**
> I just installed Wine (I think) I mean it shows up in the add/remove applications list and I can't figure out where it is or get it to run...I mean there is no icon on my desktop or drop down on my taskbar...Where is it? and how can I get it to run?

Help

Open a terminal (alt f2 and check the box that says run in terminal) and type in 

WIne[insert programname here]

for example, for deus ex, type into a terminal
wine deusex


You might need that space or not, experiment, I'm posting from a Windows machine at the moment and obviously can't really check for you.


O yeah, I forgot for a moment


type:

wineconfig

to bring up the wine options menu, where you can change whether you want a virtual desktop (which it sounds like you do) and all that kind of jazz.

Just wondering, what are you using it for anyways?

---

### Post by aktiwers on 2007-07-12
Its common that people tend to use wine when they are new to Linux. I did the same.
But I think its wrong in some sense. What is it you want to install?

Most programs has alternatives, that does the same as the Windows program, though it runs native on Linux and therefore runs a lot better.

Let us know what programs you want to install, maybe we know alternatives to them :)

EDIT: 
Godd4242
Dont you mean:
```
winecfg
``` 
?

---

### Post by Nythain on 2007-07-12
yeah, wine is pretty much a terminal app... i mean you can write links and shell scripts and whatnot, but its pretty much called from the command line.

after installing run
```

winecfg

```
as mentioned, and that will create your "windows" directory structure, usually located at:
~/.wine/drive_c/
then, once you have run winecfg you can begin installing and running apps via the command line like
```

wine /path/to/install.exe (to install something)
wine /path/to/app.exe (to run something)

```
making sure to change /path/to/whatever to the actuall path to the exe's you would like to run

Also as a side note, remember that not all windows apps are going to run, or run well under wine... its popular for gaming so most of the development of it goes into that, but it will support most windows apps... i ran World of Warcraft, uTorrent, and a few other apps with it back when i just couldnt let go of windows... now i have found free native alternatives to everything i was using wine for (minus World of Warcraft, wich i stopped playing about the time that thousands of cedega users triggered warden and got banned)

If wine wont run an app or game you have in mind, and you have the money, some other alternatives include:
Crossover - based on the wine api and focusses heavily on certain windows apps like Photoshop
Cedega - buggy fork of wine originally called WineX, it focusses primarily on gaming, and will play many games wine wont, includes an easy (i use that term loosely) to use GUI unlike wine, wich in turn makes it a very attractive alternative to most people new to linux. My opinion is its to buggy to cost money

And a last alternative if your machine is relatively decent, running windows virtually via VMWare or VirtualBox

---

### Post by Archoniam on 2007-07-12
Linux newbie? Tip for you:
To make Wine Config a shortcut on your desktop, right click on desktop...
Menu seq:
Create Launcher...
->Set to application
->Name your shortcut
->Command will be winecfg, in this case.
->Leave this empty. I forget what it does. :lol:
->Hit OK
Give it a sec... and Voila! Your icon is created! (Easier than the $200 for everything Ubuntu's got!!)

---

