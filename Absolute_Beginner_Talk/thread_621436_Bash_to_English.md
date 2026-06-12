---
title: "Bash to English"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by runemaste644 on 2007-11-23
[SIZE=5]Bash to English
[SIZE=2]This guide has some Bash commands in it and shows what it basically says to the command line. Note: Some dangerous commands are in this guide. These commands are tagged with a [COLOR=Red][SIZE=5]![SIZE=2][COLOR=Black]. If you see a command with a [SIZE=5][COLOR=Red]![SIZE=2][COLOR=Black] by it, then [COLOR=Red][SIZE=4]do not execute it **ever**.[COLOR=Black][SIZE=2] A notice will also be put by commands like that. [COLOR=Orange][SIZE=5]![COLOR=Black][SIZE=2]s indicate commands that might be dangerous, but cant really do a lot of harm.[/SIZE][/COLOR][/SIZE][/COLOR] This guide is made to teach you how to use the command line in Linux and pretty much all UNIX systems, and also to make everyone wary of dangerous commands. The commands are organized by category. Commands for applications e.g. gcalc are not included unless they are very commonly used e.g. gedit. Oh, and *something* is a file the command is run on.


[SIZE=5]File Commands[SIZE=2]

ls                                         [COLOR=White].....................................................................................................[/COLOR]Tell me everything in the directory I am in!

ln -s *something*                      [COLOR=White]...................................................................................[/COLOR]Make a symlink to *something* and put it in the directory I am in!

mkdir *something*                  [COLOR=White].................................................................................[/COLOR]Make a directory called *something*!

[/SIZE][/SIZE][/SIZE][/COLOR][/SIZE][/COLOR][/COLOR][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE][/SIZE][/COLOR][/SIZE][/SIZE][SIZE=5][SIZE=2][COLOR=Red][SIZE=5][SIZE=2][COLOR=Black][SIZE=5][COLOR=Red][SIZE=2][COLOR=Black][COLOR=Red][SIZE=4][COLOR=Black][SIZE=2][SIZE=5][SIZE=2][SIZE=5][COLOR=Orange]!   [COLOR=Black][SIZE=2]rmdir *something                [COLOR=White]..............................................................................[/COLOR]*Delete the directory *something* (but only if it is empty)!

[COLOR=Red][SIZE=5]!   [/SIZE][/COLOR]rm *something*         [COLOR=Red]
This command can be dangerous! Do not execute it unless you know what you are doing!    [COLOR=Black]
This command means: Delete *something!*

 cd /wherever/the/destination/directory/is[COLOR="White"]..................................................[/COLOR] Go /wherever/the/destination/directory/is!

pwd[COLOR="White"]....................................................................................................[/COLOR] Where in my filesystem am I???
To be continued...
[/COLOR][/COLOR][/SIZE][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/SIZE][/COLOR][/COLOR][/SIZE][/COLOR][/SIZE][/COLOR][/SIZE][/SIZE][/COLOR][/SIZE][/SIZE]

---

### Post by LaRoza on 2007-11-23
There is an announcement covering the issue of malicious commands: [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

---

### Post by LaRoza on 2007-11-23
There is an announcement covering the issue of malicious commands: [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

Your information isn't quite correct, rm and rmdir are given two different ranks for no reason. As stated, rm will not delete a directory with anything in it.

(I wonder why this came twice?)

---

### Post by runemaste644 on 2007-11-23
Who says you have to delete a directory? rmdir can only delete directories. rm can delete files. rm -r will delete stuff recursively. i just put the warning tags so i would not be accused of posting malicious commands.

---

### Post by runemaste644 on 2007-11-24
[SIZE=5]Running as Root
[SIZE=4][COLOR=Red]WARNING! Running as root can be dangerous. Run as root only if necessary. Only install packages from trusted sources.
[COLOR=Black]
[SIZE=2]sudo *command*[COLOR=White]................................................[COLOR=Black]Run *command* as root.
Note: Never use the sudo command for graphical apps.
gksu *gnome-app*[COLOR=LemonChiffon]......[COLOR=White]..................................[/COLOR]......[COLOR=Black]Start a graphical application native to Gnome as root.
Note: Never use gksu for non-graphical or applications native to KDE.
kdesu *kde-app[COLOR=White].................................................[/COLOR]*[COLOR=White][COLOR=Black]Start a graphical application native to KDE.
Note: Never use kdesu for native Gnome apps or non-graphical apps.
sudo -i[COLOR=White].............................................................[COLOR=Black]Prompt me for my password and make me root if I have administrative privileges and enter my password correctly.

If I am missing any commands related to this category, PM me and I will add it ASAP. [/COLOR][/COLOR]
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/SIZE][/COLOR][/COLOR][/SIZE][/SIZE]

---

### Post by runemaste644 on 2007-12-18
**[SIZE=5]Special forms of ls[/SIZE]**[SIZE=5][I][SIZE=1]
ls has many commands named after it
[/SIZE][/I][SIZE=1][SIZE=2]lsmod[COLOR=White]............................................[COLOR=Black]List installed kernel modules
lspci[COLOR=White]..............................................[COLOR=Black]List known hardware
lsusb[COLOR=White].............................................[COLOR=Black]List connected usb devices[/COLOR][/COLOR]
[/COLOR][/COLOR][/COLOR][/COLOR][/SIZE][/SIZE][/SIZE]

---

