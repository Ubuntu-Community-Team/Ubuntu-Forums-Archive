---
title: "how to make launcher with 2 commands"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-08
Hi
The problem is I don´t know how to make launcher from azureus. To start azureus I allways type cd /home/user/azureus/ and then ./azureus into terminal. Is it possible to make a launcher that will start azureus just by clicking on it?

---

### Post by krazykirk on 2006-08-08
Hi there,

I'm sure that making a launcher will be complicated, even I don't know how. But i have azureus and it works fine!

I'm assuming that you downloaded the tar.gz file from the website and just extracted it, but it is in the repos. Just open up a terminal and type

sudo apt-get install azureus

and that should install and configure azuerus for you! And you will also get a menu entry! Yay!

---

### Post by timhaughton on 2006-08-08
Hi, there's a couple of things going on here. 

First off, you could just type /home/user/azureus/azureus to start the program.

You could add /home/user/azureus/azureus to your shell's PATH variable, which tells the shell where to look for executables.

But as an earlier poster said, you should really install it via apt-get. Post back if you still have problems.

---

### Post by Jagot on 2006-08-08
Mine shows up in the Internet section in the Applications menu.  If it is installed correctly then you should be able run it from alt+f2 or the terminal by just typing azureus.  If you want to create a launcher then the command (again if installed correctly) would be:

```
azureus %U
```

---

### Post by vaazu on 2006-08-08
The command /home/user/azureus/azureus worked perfectly

---

### Post by tony_tj3 on 2006-08-08
Another option could be to cp /home/uname/azureus/azureus /usr/bin/azureus, that would allow you to run it by just enterign teh command azureus, then you could add it to apps>>net, by creating a script like this:

sudo gedit /usr/share/applications/azureus.desktop

enter this in the new file:
[Desktop Entry]
Encoding=UTF-8
Name=azureus
Comment=Azureus Bittorrent Client
Exec=azureus
Terminal=false
Type=Application
StartupNotify=true
Icon=/<<WHEREVER YOUR AZUREUS ICON IS>>
Categories=Application;Network;

save the file.

---

