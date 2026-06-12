---
title: "[SOLVED] How do I create a Launcher for a script?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by crjackson on 2008-01-27
I need a good Home Inventory program.  I downloaded one called Attic Manager.  It doesn't need to be installed, you just unpack it and run a script.  How can I make a Launcher for my desktop so that I don't have to open a terminal and navigate to the folder, then run the script?

Here is the contents of the script that will launch the program ONLY from inside the current folder.

```
#!/bin/bash
export FIREBIRD=.
export LD_LIBRARY_PATH=.
export ATTIC_DIRECTORY=`pwd`
./attic
```

---

### Post by Majorix on 2008-01-27
Make sure xterm is installed first:
```
sudo apt-get install xterm
```
Then, open up alacarte:
```
alacarte
```
In there, click add, and fill in this info:
```
xterm -e "cd PathToTheScript; ./ScriptName"
```

---

### Post by Dr Small on 2008-01-27
I'm pretty sure xterm comes preinstalled because of xorg. ;)

---

### Post by steveneddy on 2008-01-27
OK - how about the GUI way.

First make the script able to be run as a program by right clicking the file, go to properties and check the box for executing file as program under the permissions tab.

Next, go to the desktop or the taskbar where you want the launcher and right click and select Add to Panel - or desktop.

Click Custom Application Launcher.

Name the Launcher.

Browse to the file location.

Choose an icon.

click ok and try it out.

---

### Post by crjackson on 2008-01-27
> **steveneddy said:**
> OK - how about the GUI way.

First make the script able to be run as a program by right clicking the file, go to properties and check the box for executing file as program under the permissions tab.

Next, go to the desktop or the taskbar where you want the launcher and right click and select Add to Panel - or desktop.

Click Custom Application Launcher.

Name the Launcher.

Browse to the file location.

Choose an icon.

click ok and try it out.

This One Doesn't work at all.  The script can be executed by clicking on it, but it will only work from the working directory.

---

### Post by steveneddy on 2008-01-27
I run several scripts this way. I don't know why it wouldn't work for you.

---

### Post by crjackson on 2008-01-27
> **Majorix said:**
> Make sure xterm is installed first:
```
sudo apt-get install xterm
```
Then, open up alacarte:
```
alacarte
```
In there, click add, and fill in this info:
```
xterm -e "cd PathToTheScript; ./ScriptName"
```

Okay, so alacarte seems to be the same as right click on the Applications menu and clicking on edit.  Correct?

I added an item and it didn't work.  Here is the command I entered into the properties:
```
xterm -e "cd /home/charles/attic_manager; run-attic.sh"
```

Actually, this DID work.  I forgot to prefix the script with "./"

---

### Post by crjackson on 2008-01-27
> **Dr Small said:**
> I'm pretty sure xterm comes preinstalled because of xorg. ;)

Yes, I get a terminal screen when typing xterm in a standard terminal.  So it's installed.

---

### Post by crjackson on 2008-01-27
> **Majorix said:**
> Make sure xterm is installed first:
```
sudo apt-get install xterm
```
Then, open up alacarte:
```
alacarte
```
In there, click add, and fill in this info:
```
xterm -e "cd PathToTheScript; ./ScriptName"
```

[SIZE="4"][FONT="Comic Sans MS"][COLOR="Red"]Is there anyway to have it open the program without it showing the open terminal?[/COLOR][/FONT][/SIZE]

---

### Post by crjackson on 2008-01-27
Is there anyway to have it open the program without it showing the open terminal?

Anybody?

---

### Post by seventhc on 2008-01-27
create the custom launcher as mentioned above, put the full path in the command box..
/home/you/./script.sh
didn't work, it opens and closes
I went to properties tried as open as an app and in terminl
did chmod 755
hmmmm
tried it as ./script.sh too, nothing yet.
btw, I named it script.sh ;)

---

### Post by crjackson on 2008-01-27
> **seventhc said:**
> create the custom launcher as mentioned above, put the full path in the command box..
/home/you/./script.sh
didn't work, it opens and closes
I went to properties tried as open as an app and in terminl
did chmod 755
hmmmm

It does open the app as wanted, but it leaves the terminal screen open.

---

### Post by seventhc on 2008-01-27
I can get it to open but it says there was an error creating the child process, is that b/c I don't have thunderbird and the others, or is that just an error b/c it is wrong?

---

### Post by crjackson on 2008-01-27
Here's the xterm output:

```
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
/home/charles/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'

```

---

### Post by seventhc on 2008-01-27
> **crjackson said:**
> It does open the app as wanted, but it leaves the terminal screen open.
ahh ok, I thought it wasn't running at all. 8)
back to the drawing board. :D
do you have it set to run in terminal or as application under properties of the script?
Maybe try it as an app???

---

### Post by crjackson on 2008-01-27
> **seventhc said:**
> ahh ok, I thought it wasn't running at all. 8)
back to the drawing board. :D

It' running but xterm throws errors, and I would like the xterm to hide or close instead of just hanging around if possible.

---

### Post by seventhc on 2008-01-27
here is a link that might help
[http://ubuntuforums.org/archive/index.php/t-548947.html](http://ubuntuforums.org/archive/index.php/t-548947.html)
I think they put exec script.sh but give it a look
I don't think that works, You might find someone in the programming part of the forums who might have a better idea.

---

### Post by seventhc on 2008-01-27
I just did a script that opens firefox, no terminal opens. I was getting errors, not sure why but when I browsed to the file they stopped.( i mean when entering the path)
It is different from yours, but it is still running from the script and no terminal
I even have it set to open in terminal and only firefox opens, but I can't reproduce yours on my machine b/c I don't use thunderbird, etc.
I am not sure if it should matter though.

---

