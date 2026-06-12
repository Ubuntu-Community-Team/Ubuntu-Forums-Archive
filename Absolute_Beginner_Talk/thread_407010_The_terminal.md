---
title: "The terminal"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by snobby500 on 2007-04-11
Hi

     Im new to ubuntu and I was just wondering. Whats so good about the terminal, dont get me wrog im not saying its bad, but whats so good about it, as I dont know. I cant see it being faster, or much faster, especially when moving many files from one folder to another, surely navigatng to a place is mnuch quicker on the desktop? Plz tell me what stengths uisnig the terminal has. And just to make sure, ubuntu uses  bash rite? (bourne again shell?).

thanks

---

### Post by Bachstelze on 2007-04-11
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

### Post by Ganda_Melga on 2007-04-11
> **HymnToLife said:**
> [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)


Great link! Thanks a lot! :guitar:

---

### Post by Maestro23 on 2007-04-11
CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Bachstelze on 2007-04-11
> **snobby500 said:**
> I cant see it being faster, or much faster, especially when moving many files from one folder to another, surely navigatng to a place is mnuch quicker on the desktop?

You hink so ? All right, so let's say you want to move only the mp3 files from /some/folder to /other/folder/, you ;

-> Open your file manager
-> Browse to /some/folder
-> Select all the files
-> Click "Cut"
-> Move to /other/folder
-> Click "Paste"

While I just type this in my terminal :

```
mv /some/folder/*.mp3 /other/folder
```

First way is faster, really ?

---

### Post by jem7v on 2007-04-11
- If your X server breaks and you don't have access to a GUI (graphic user environment - i.e., your Desktop) you can usually fix it from the command line. To switch to one of these virtual terminals, press Ctrl+Alt+F1, or F2, or F3... etc. F1-F6 are virtual terminals you can work in and F7 is where your GUI usually resides.
- If a script cannot run while your X server is operating, such as the official NVidia driver installer, you'll Have to do it from a virtual terminal.
- You can ask your system lots of questions about what is or isn't working properly from the terminal. Making a user interface to report all this data would be tedious and consume lots of space on the screen if you used it, and it would have to display lots of information that may or may not be specific to what you were trying to do. By just checking in a terminal, you only have to ask the computer to tell you the information you Need rather than everything.
- You can compile programs from the command line.
- You can use it to run programs with odd arguments that they might not usually be loaded with.
- You can use it to pipe information from one program to another and do nifty, clever things.
- It looks impressive and mysterious to people who aren't very tech-savvy.

---

### Post by snobby500 on 2007-04-11
haha, i c what u mean, but its not faster in all cases, is tht rite? u just kinda have it hanging around for when its needed? and thanks a lot 4 all the links n stuff. gd examples btw. I like the last reason - it looks cool ;)
thx

---

### Post by Bachstelze on 2007-04-11
Yes, I always have a terminal ope, because I use it for everything that doesn't absolutely requires a GUI

---

### Post by Maestro23 on 2007-04-11
> **HymnToLife said:**
> Yes, I always have a terminal ope, because I use it for everything that doesn't absolutely requires a GUI

Same here.

---

### Post by eltaito on 2007-04-11
you by no means "have to" become familiar with using the terminal but like everyone else here I'd highly recommend it...when I first came over to Linux from Windows I found it kind of scary but after using it for a while I became addicted......the command line provides a short-cut for almost every task.....it really is amazing how fast you can get things done once you break your dependency on the mouse and gui's ........I'm somewhat of a terminal junkie now, I even stopped using my mouse for virtually every other program I use frequently as well...especially web browsers, short-cut keys make web browsing so much more enjoyable but I'm rambling and getting off-topic as I so often do....definitely check out that "linuxcommands.org" link posted above..thats where I first learned basic terminal usage and I haven't looked back since :D

---

### Post by aysiu on 2007-04-11
It's faster for me to install ten programs with the command-line than with the graphical user interface: ```
sudo apt-get update && sudo apt-get install skencil krita xaralx inkscape gimp scribus banshee kword thunar firefox -y
``` That command took me about fifteen seconds to type (had to think of the names of all the programs). How fast can you install all those programs by pointing and clicking? Please time yourself. Thanks.

---

