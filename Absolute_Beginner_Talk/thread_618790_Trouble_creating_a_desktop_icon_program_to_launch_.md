---
title: "Trouble creating a desktop icon program to launch a command ..."
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-20
How do I launch a program by clicking on an Icon?

I tried to create a launcher for this command:

/etc/init.d/samba restart

so that I can start Samba by clicking on an Icon from the desktop.  
But, I can't seem to get it to work.

Carl

---

### Post by Dr Small on 2007-11-20
Maybe,
```
sudo /etc/init.d/samba restart
```

??

---

### Post by scrooge_74 on 2007-11-20
probably should be gksudo since it will start in the GUI

---

### Post by Dr Small on 2007-11-20
Gksudo is for launching Graphical Root Applications. The command he wishes the invoke, runs in a command line, which should not need gui for.

Dr Small

---

### Post by cwmoser on 2007-11-20
I get the error:

There was an error launching the application.
Details: Failed to execute child process "gksudo /etc/init.d/samba restart" (No such file or directory)

Carl

---

### Post by websnail on 2007-11-20
gksudo can launch a command by Alt+F2 , with a GUI you can type your root password. with gksudo you must't open a terminal to input password .

---

### Post by cwmoser on 2007-11-21
What if all I wanted to do was to create an icon on the desktop that I can click on that would open a command prompt and automatically run say ls -l /tmp

If I can get this to work, I can use it as a model to create other more useful functions.


Carl

---

### Post by websnail on 2007-11-21
> **cwmoser said:**
> What if all I wanted to do was to create an icon on the desktop that I can click on that would open a command prompt and automatically run say ls -l /tmp

If I can get this to work, I can use it as a model to create other more useful functions.


Carl
try this:
gedit rsamb,type in
```
#!/bin/sh
gksudo /etc/init.d/samba restart
```
save it , and chmod +x rsamba
then double click it , a dialog pop out ask you root pssword and your command runs.
or in a console just keyin ./rsamba
after pwd dialog , you can see:```

\ * Stopping Samba daemons...                                            [ OK ] 
 * Starting Samba daemons                                                [ OK ] 
```

I'v checked , it works .

---

### Post by cwmoser on 2007-11-21
Websnail, thanks that got it working.  Appears the trick is to put the commands in a shell file, make the file executable, and in the launcher give a full path to the location of the shell file.

Now, is there a command I can use that will give me some feedback that the program actually ran -- like say a message box?  Sorta like if I could do something like this in the shell file:

#!/bin/sh
gksudo /etc/init.d/samba restart
MSGBOX "Samba has been started"

where a messagebox will popup on the desktop?

Thanks

Carl

---

### Post by cwmoser on 2007-11-21
I did think of this ...

#!/bin/sh
gksudo /etc/init.d/samba restart
espeak "Samba services has been started"


... that is if you like for your computer to talk back to you :-)

Carl


Still, would be nice to have a popup message box.

---

### Post by websnail on 2007-11-21
You can use this:
> zenity --info --text="Samba services has been started"

---

### Post by cwmoser on 2007-11-21
OK, this is what I've finally come up with:


#!/bin/sh
gksudo /etc/init.d/samba restart
espeak "Samba services have been started"
zenity  --info  --text="Samba services have been started!!"


espeak = audible announcement
zenity = popup message box on desktop

Carl

---

