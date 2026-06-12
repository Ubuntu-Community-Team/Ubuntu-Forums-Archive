---
title: "[SOLVED] open file in gnome terminal?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-12-11
i'd like to be able to punch in something like...

```

gnome-terminal && cd /home/niklas/Desktop/Cwiid.sh

```

to open a terminal that will automatically cd to that directory and run a file.  is this possible?

---

### Post by nikoPSK on 2007-12-11
as a script most likely, but I am not gifted in scripting...:(

---

### Post by Dr Small on 2007-12-11
Try this:
```
sh /home/niklas/Desktop/Cwiid.sh
```
and make a launcher to it, and check to open it in the terminal ;)

---

### Post by spai on 2007-12-11
> **Dr Small said:**
> Try this:
```
sh /home/niklas/Desktop/Cwiid.sh
```
and make a launcher to it, and check to open it in the terminal ;)
Hmm just a small doubt,
How do we create a launcher?

---

### Post by Dr Small on 2007-12-11
Right click on the desktop and create a launcher.

---

### Post by Niklas Schröder on 2007-12-11
but what do i type in terminal or put in a .sh script that'll work?  i want my script to open another terminal window and immediately open/run a new script.

---

### Post by Perfect Storm on 2007-12-11
Easy enough. Make a new file called eg. **Cwiid-script.sh**. Lets say it's placed on your Desktop.

```
cd ~/Desktop
nano Cwiid-script.sh
```

add the following:

[b]#!/bin/bash
sh ~/Desktop/Cwiid.sh[/b]

save [ctrl]+[o]
exit [ctrl]+x]

```
chmod +x Cwiid-script.sh
```

Now point a launcher to the script.
The command launcher would be:
sh /home/<name>/Desktop/Cwiid.sh

---

### Post by Niklas Schröder on 2007-12-11
and can i just stick that line of code in one of my scripts and have the script open a new terminal?

---

### Post by Perfect Storm on 2007-12-11
When you make a script, it will run the commands as it was something you wrote in the terminal.

---

### Post by mali2297 on 2007-12-11
This will open xterm, run the script and then hold the window open.
```

xterm -hold -e sh /home/niklas/Desktop/Cwiid.sh

```
The current directory will not be /home/niklas/Desktop though, is that important?

---

### Post by TheViper on 2007-12-11
Has anyone had any issues with 7.10 telling you you do not have user privliges? Can't edit the name of a file.

---

### Post by mali2297 on 2007-12-11
> **TheViper said:**
> Has anyone had any issues with 7.10 telling you you do not have user privliges? Can't edit the name of a file.

Use sudo or gksudo, see
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

By the way, you are stealing the thread from Niklas here.

---

### Post by Niklas Schröder on 2007-12-11
this...

```

xterm -hold -e sh /home/niklas/Desktop/Cwiid/Cwiid_Automator.sh

```

is what i wanted.  ;)  thanks for the headstart mali!  but is there any way to do this in gnome-terminal (out of curiosity...)?

---

### Post by dutch1918 on 2007-12-11
Sorry to hi-jack this however I need some help also in making a script that will do the following:

```

cd /home/ldevries/IBJts
java -cp jts.jar:pluginsupport.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame .

```
Thanks for the help

---

### Post by Niklas Schröder on 2007-12-11
two hijacks in 10 minutes.  that's gotta be a new record...

---

### Post by mali2297 on 2007-12-11
An alternative..
```

xterm -e "cd /home/niklas/Desktop/Cwiid ; sh  Cwiid_Automator.sh ; bash"

```
This will change the current directory and also allow you to use the terminal after the script is done.

I can't help you with gnome-terminal.[-(

---

### Post by Niklas Schröder on 2007-12-11
no worries about gnome-terminal.  but is there any way to make a launcher start xterm instead of gnome-terminal?

```

sh /home/niklas/Desktop/Cwiid/Cwiid_Automator.sh

```

that's my current menu launcher which starts gnome-term.  i'd rather it started that file in xterm...

---

### Post by mali2297 on 2007-12-11
> **Niklas Schröder said:**
> no worries about gnome-terminal.  but is there any way to make a launcher start xterm instead of gnome-terminal?

```

sh /home/niklas/Desktop/Cwiid/Cwiid_Automator.sh

```

that's my current menu launcher which starts gnome-term.  i'd rather it started that file in xterm...

Just run **xterm -e ...** as a custom command, do not check the box "run in terminal".

---

### Post by Niklas Schröder on 2007-12-11
nvm.  found out i can just throw this in and it'll work.  ;)

```

xterm -hold -e sh /home/niklas/Desktop/Cwiid/Cwiid_Automator.sh

```

---

### Post by Niklas Schröder on 2007-12-11
lol.  you beat me to it.  ;)  thanks for the help guys!  :D

---

### Post by dutch1918 on 2007-12-11
> **dutch1918 said:**
> Sorry to hi-jack this however I need some help also in making a script that will do the following:

```

cd /home/ldevries/IBJts
java -cp jts.jar:pluginsupport.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:rss.jar -Xmx256M jclient.LoginFrame .

```
Thanks for the help

well I was able to stumble through it and made the bash script. Now if I can figure out how to have the terminal start minimised that would be great

---

### Post by mali2297 on 2007-12-11
> **dutch1918 said:**
> well I was able to stumble through it and made the bash script. Now if I can figure out how to have the terminal start minimised that would be great

This might work
```

xterm -title foo -e "wmctrl -r foo -b add,hidden ; sh bar.sh ; bash"

```

You need to install the package **wmctrl** from the repositories.

---

### Post by stroyan on 2007-12-11
gnome-terminal also has a -e option.  But gnome-terminal does not pass the -e argument to a shell.
So you need to add an explicit shell if you want to do multiple things in one command line, such as
changing directory and then running a command.  Here is an example using bash -c to parse the
sequence of commands.

gnome-terminal -e 'bash -c "date;cd /tmp;ls;bash"'

---

