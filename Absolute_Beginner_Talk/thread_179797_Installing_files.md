---
title: "Installing files"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by benuski on 2006-05-20
Is there a guide, or could someone whip one up really quick, of how to go step by step from a source code file to an installed program that works?  I'd like to keep as little as possible on my partitioned interal hard drive, and keep all the things that are ubuntu specific on my external hard drive.

---

### Post by barbarian on 2006-05-20
hi, probably here?

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Sef on 2006-05-20
here's another one:

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

### Post by catlett on 2006-05-20
There are links in my signature but it is pretty straight forward once you understand the process.
The first thing you need is the application build-essential. So first do ```
sudo apt-get install build-essential
```
Next is to acquire the tar file. THis explanation is for compiling from code not dealing with debs or scripts. The source packages are in compressed tar files. For sake of arguement we'll call the package widget.
Download the wigdget tar file (it doesn't matter if it tar.gz or tar.bz when using this method). Firefox by default downloads to your desktop. We'lll assume that is the case and put it into the example.
With the widget.tar.gz file on the desktop move your mouse over it and right click. Fron the option menu choose "extract here". This will make a folder "widget" on your desktop.
To compile we have to be in that folder "virtually" . You do this from the terminal. Open the terminal and type```
 cd /home/benuski/Desktop/widget
``` This puts the terminal in the folder widget. (cd=change directory, the desktop is actually in your home folder.  so to get there you have to go through  the home folder, through the user folder, through Desktop and arrive in widget)
Once the terminal is at /home/benuski/Desktop/widget ~$ there are 3 commands to compile. The first command is ```
./configure
``` The next command is ```
make
``` And finally ```
sudo make install
``` That is it. Sometimes there are dependency issues and even though you compiled correctly the file can't be used on your setup. You can try and install the dependencies. If you resolve the dependencies, the package can be installed.
If you don't have the debian menu installed you might not see the application in the menu. You can always launch an application from the terminal by entering it's name ```
widget
```

---

