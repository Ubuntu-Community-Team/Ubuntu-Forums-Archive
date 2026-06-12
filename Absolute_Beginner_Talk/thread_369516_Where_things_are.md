---
title: "Where things are?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by tarek on 2007-02-24
Hi, 

I "was" a windows user, recently switched to linux - ubunut edgy.

I like the package manager, but would like to learn how to install programs, where is "program files", "windows dir", etc.

Can somebody tell what is somewhat equal to "Program Files"? say I downloaded a zip/tar file, where do I unzip/tar it and to let the system know about it?

Thanks,
tk

---

### Post by aysiu on 2007-02-24
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) should help.

---

### Post by Tomosaur on 2007-02-24
The linux directory structure is very different to Windows. There is no real 'program files' directory, no 'windows dir' directory. Linux is quite literally like a tree. The root directory ('/') is the base of the tree, and the directories inside that are the branches. In Windows - software files are 'grouped together' according to individual program names. i.e: all of the files - the binary files, the documentation, sounds etc, are all grouped together in that program's folder. In linux, these various parts are seperated. It can seem illogical at first - but there are benefits. In Windows you will invariably end up with lots of libraries and stuff which do the same thing. In linux, this is kept to a minimum - because programs share libraries / sounds / icons and such. Binary files (the actual programs) are normally kept in /usr/bin, while images can be in /usr/share. It will take some getting used to, but it actually makes quite a bit of sense. The normal installation method is to download a package (a .deb file). Double click it, and the installation program will handle where it goes. However, you can find thousands and thousands of software packages by clicking Applications > Add/Remove, or System > Administration > Synaptic Package Manager. This means you don't need to concern yourself with how to install programs, just click the ones you want.

Occasionally you may want to download a program from the web. If the program is in a .deb file, you can normally just double click it and the computer will install it itself (think of it similar to Setup.exe in windows). However, other programs will come in a .zip file. These you are likely required to compile and install yourself. To do this you will need the 'build-essential' package (which you can download via synaptic). You then need to open up a terminal, change to the directory you extracted the package to, and type:
```

./configure
make
make install

``` This will install that program inside that directory. Alternatively, you can use 'sudo make install' in place of that last line, to install the program system-wide (so that everyone can use it). Keep the directory handy, so you can do 'make uninstall' or 'sudo make uninstall' to remove it if you don't want to keep it. That is the 'normal' compilation method, but it occasionally varies slightly - you'll have to read the README file, or the INSTALL file which will normally be in the archive.

However - it's better to just stick to Add/Remove or Synaptic - you're unlikely to need anything that isn't available through that.

---

### Post by robophred on 2007-02-24
Ah, this confused the heck out of me when I started with debian.
In fact, it still does, but to a lesser extent.

Everything I have installed from the package manager has added itself to the applications menu.  Everything else I have installed from tutorials, which said what commands to use them.

In the terminal, you can try to find the program by typing a part of its name in the terminal and hitting the 'tab' key twice.
Example is when I type 'apt' and hit tab twice, it shows me apt-cache, apt-config, apt-get, apt-mark, and others.

It seems that most programs install to /usr and most have their config files either in your home directory as hidden files (in gnome, do "view->show hidden files" or ctrl-h in the file browser, in a terminal, do "ls -a", which generally means "list files/folders, all")

You can get information on most programs by using the "man" (probably short for 'manual') command.  Try "man <program name>" in the terminal.  For example: "man aptitude".  Generaly the program name will be what you use when using aptitude, but NOT what is used in the add/remove window.

---

### Post by tarek on 2007-02-24
Thanks.

I installed Azureus using the package manager but it was an old version so I download the latest and untared the files under /usr/lib then created a symbolic link in /usr/bin then added a shortcut to  the application -> internet menu.

Should I have stored the files somewhere else or /usr/lib is OK?

thanks again.

---

### Post by robophred on 2007-02-24
/usr/lib seems to be home to common library files (linux equivalent of dll files).  It is probably the same as installing a windows program into C:\windows\system32, but it will still function.  Best to copy the folder to another folder under /usr, making your own if you need to (via the terminal command mkdir, do "man mkdir" for more information).

<edit>
I just looked into /usr/lib, apparently it is home to both libraries and programs.  Guess it isnt reserved for libraries, but all in all, I would make a new folder for it or its catagory under /usr.

---

### Post by tarek on 2007-02-24
Sounds good. This way my programs will not conflict with the package manager's programs if I install something.

thanks

---

### Post by aysiu on 2007-02-24
> **tarek said:**
> Sounds good. This way my programs will not conflict with the package manager's programs if I install something.

thanks
Actually, if you truly want them separate, you can install them to /opt or /usr/local/bin

---

### Post by tarek on 2007-02-24
> **aysiu said:**
> Actually, if you truly want them separate, you can install them to /opt or /usr/local/bin

What does opt mean?

---

### Post by annda on 2007-02-24
maybe you don't need it but it's still one of my favorites:
```

whereis some_program_name
```

good if you want to make shortcuts or create launchers but can't remember where the file is.

more detailed than whereis is locate. but it uses a database to store file locations (not only executables, good for config files too), so if you install / create new files frequently, you may need to to run

```
sudo updatedb
```

first.

---

### Post by aysiu on 2007-02-24
> **tarek said:**
> What does opt mean?
I don't know. My guess would be *optional*.

---

### Post by robophred on 2007-02-24
Gnome/Ubuntu has a search feature built in, you can access it by going under "places->search for files", or just hitting ctrl+f after clicking anywhere on the desktop.

You can also add the "deskbar" to the panels, which is probably the coolest feature ever to grace a start bar or panel anywhere.

Right click the gnome panel (A panel is the gnome equivalent of the windows taskbar, except a heck of a lot more functional), and hit "Add to panel", select the "Deskbar" icon under "Accessories".  Once you place it, right click it and select Preferences, and you can select which 'searches' to have it do.  
When you click the icon, it will show the search box, and as you type it will search out based on what you have selected (programs, files, dictionary definitions, et al).
You can also select the view tab under preferences, and give it a keyboard shortcut.

I had to shut off the xwindows session and to apt-get upgrade in order to get the deskbar to show up in the add to panel screen, however.  I saw it when I installed ubuntu to an old laptop yesterday, and it didn't show up in the normal gnome update manager...

---

### Post by squig on 2007-02-24
This is such an excellent explanation that I think I'm going to copy it and save it somewhere extra special!!!

---

### Post by tarek on 2007-02-24
Nice tool.

---

