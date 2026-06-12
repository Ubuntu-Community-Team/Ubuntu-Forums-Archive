---
title: "wine"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Taren on 2007-01-09
hello i have installed wine on my ubuntu and would like to know how you get it to work i downloaded it from wineHQ but i can't find anything from there to tell me how to use it

---

### Post by livinginx on 2007-01-09
> **Taren said:**
> hello i have installed wine on my ubuntu and would like to know how you get it to work i downloaded it from wineHQ but i can't find anything from there to tell me how to use it

Did you already install it or just download it from WineHQ?

If you haven't truly installed it, you can do
```
sudo apt-get install wine
```

Which will properly install it and allow you keep it updated.

After you do that, in terminal, type: winecfg
This will create your directory.  But don't do it as sudo. After it creates the directory, it will open up the Wine Configurator.  Most stuff doesn't need to be changed in there right away.

---

### Post by deadgobby on 2007-01-09
Wine is all so in Synaptic too. 
Gobby

---

### Post by SoggyCornflake on 2007-01-09
> **Taren said:**
> hello i have installed wine on my ubuntu and would like to know how you get it to work i downloaded it from wineHQ but i can't find anything from there to tell me how to use it
There's an Ubuntu package for wine that you may want to install, but I don't know if it has any thing in addition to what you can get from winehq.

You need to run winecfg to setup your wine environment.  when you want to run a windows program, open terminal session and type ```
wine foo.exe
```

assuming it runs, then treat it like a windows program.  From what I've experienced, lots of programs have issues that take a lot of tweaking.  I can't help you with that.

---

### Post by 3rdalbum on 2007-01-09
> **Taren said:**
> hello i have installed wine on my ubuntu and would like to know how you get it to work i downloaded it from wineHQ but i can't find anything from there to tell me how to use it

Press Alt-F2 and type

```
winecfg
```

If there's anything in there that needs changing, change it. Otherwise, keep it the same. Close the window.

In a terminal, navigate to the directory that contains the Windows program you want to use, then type "wine *programname.exe*. For instance, if you had a CD with "setup.exe" on it, you'd type:

```
cd /media/cdrom
wine setup.exe
```

The program will start.

Wine creates a fake Windows hierarchy inside your home directory. If you installed, say, Firefox within Wine, you would get to the Firefox by typing:

```
cd "~/.wine/drive_c/Program Files/Mozilla Firefox/"
wine firefox.exe

```

---

### Post by KaeseEs on 2007-01-09
EDIT:  this post mostly duplicates what's been said already.  I type slow.



To get wine installed properly, do what the above poster (livinginx) said.

Once it's installed and you've run winecfg, it's pretty simple to use Windows software on Linux.  Basically, this is what goes down:

1)  WINE makes a folder, located at ~/.wine  .  This is where all your WINE stuff will go.

2)  WINE makes a subfolder, located at ~/.wine/drive_c  .  This is where all your Windows software will go; it is a fake C:\ drive.

3)  To run a program, first install it in your WINE environment.  From the command line, run:```
wine <location of installer>
```A common scenario is to pop the CD in your drive and run the installer from it:```
wine /media/cdrom/setup.exe
```

4)  Once you've installed a program, you can run the program directly:```
wine ~/.wine/drive_c/location/of/program.exe
```

I hope this helps.

---

### Post by Atomic Dog on 2007-01-09
That brings up something I have wondered... Why is the wine folder hidden?

---

