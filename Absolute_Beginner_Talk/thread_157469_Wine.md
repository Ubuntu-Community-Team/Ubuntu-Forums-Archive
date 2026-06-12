---
title: "Wine?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-09
Where can I get Wine and what does it do?  Does it let me run Windows XP applications? Please leave me a download link or directions on how to download, and also explain what it does, I've been hearing a lot about it.

---

### Post by christhemonkey on 2006-04-09
You can install it with synaptic or from a terminal type:
```
sudo apt-get install wine
```
(Will only work if you have the universe repostiories enabled)
It adds a windows emulation layer or something, basically lets you run windows stuff.  Allthough it doesnt work with lots of programs and can be a right hassle to get working.

---

### Post by dylonium on 2006-04-09
How do I enable universe repositiories and whats a synaptic or terminal type? Explain- IM A NEWB :)

---

### Post by christhemonkey on 2006-04-09
Ok, ill try and explain:

For adding all extra repositories:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Syanptic is a wonderful program that lists all the software you can install from ubuntu. a screenshot:
[http://www.flickr.com/photos/msabramo/74552037/](http://www.flickr.com/photos/msabramo/74552037/)
Is under system menu and then administration.

A terminal is a command line type thing, a screenshot:
[http://www.flickr.com/photos/sog/109107604/](http://www.flickr.com/photos/sog/109107604/)
Located in applications and then the top one, i forget its name...

---

### Post by Sef on 2006-04-09
To get to Synaptic:  System > Administration > Synaptic Package Manager > Search > type in WIne > highlight Wine > click apply.

To get to the terminal: Applications > Accessories > Terminal 

To enable the repositories: [https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

You can add applications through either the terminal or Synaptic.  The terminal uses apt-get to download applications. Synaptic is simply a graphical interface for apt-get.

---

### Post by dylonium on 2006-04-09
Can you do this in live? Please reply ASAP!

---

### Post by christhemonkey on 2006-04-09
Not a clue, dont have a live cd to hand.  Why not just try and find out?

---

### Post by halitech on 2006-04-09
I don't see why not, I know you can install most other things when using a live cd, might be a little tricky though on getting other things to run inside Wine.

---

### Post by Sutekh on 2006-04-09
[quote=dylonium]Can you do this in live? Please reply ASAP![/quote]
Not really ASAP, sorry ;)


 - Yes you can install wine using the LiveCD, but to get it you don't enable the universe repository (the version of Wine in there is old), you should add the WineHQ repository.

- Open a terminal window (from the Menu; Applications -> Accesories -> Terminal), and issue the commands
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo nano /etc/apt/sources.list
``` - This will backup your apt-get repository sources list, so you can always change it back, and then allow you to edit the list.

- To install wine you will need the wine repository; add these lines to your sources.list
```

deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/
``` - Then save the file (Ctrl+O) and exit (Ctrl+X).

 - Update the repositories and install wine using
```
sudo apt-get update
sudo apt-get install wine
```

 - Once wine is installed you should run **winecfg** to setup options such as sound, extra drives, etc.
```
winecfg
```

 - To install a game/program use wine in the following manner
```
wine /path/of/program.exe
```

 - For example running the setup.exe program on a CD-ROM
```
wine /media/cdrom0/setup.exe
```


 - If there is a particular program that you are interested in, you should have a read of the [Wine Application Database](http://appdb.winehq.org/) to see how it runs with wine and find out about any issues that you may encounter.

---

