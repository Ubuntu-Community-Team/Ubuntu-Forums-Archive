---
title: "Intalling Programs without connection?"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by PumpkinSonnema on 2006-01-04
Hi there,
   I'm new to Ubuntu.  Love it so far.  I have a winmodem so whenever I'm connected, I'm in Windows.  

   The only problem I've been having is putting programs that I've downloaded online with windows, into Ubuntu.  I can get the tar.gz file onto the Ubuntu partition, but can't seem to install it from there.  I've seen some threads about command line installing stuff, but I have no idea how to get the command line up from Ubuntu. 

  Anybody know?

Thanks,
Pumpkin

---

### Post by hillbilly on 2006-01-04
I assume you are in GNOME. Go to system->applications->terminal. This will open up a terminal for you with the command line(CLI) prompt. On the basics of installing programs from the command line check out this link 
[http://www.linuxquestions.org/questions/showthread.php?t=45094](http://www.linuxquestions.org/questions/showthread.php?t=45094)

Or try googling with the keywords "Installing command line linux" It should throw up some good links which would help you more.

And of course you can always come back here :D

---

### Post by joshuapurcell on 2006-01-04
There are at least a couple of ways to bring up the console:

-Use the Menu: Applications -> Accessories -> Terminal
-Hit ALT-F2, then type gnome-terminal (then press enter).

Once you have a terminal up, you will need to move to the directory that your install files are located in. At first you are in your home directory by default, so if your install files are located in /tmp/downloads, then type:```
cd /tmp/downloads
```
Now you can type **ls** to see the files and make sure you are in the correct spot. Use the following command to decompress and unarchive the tar.gz files (*where NameOfFile is the actual name of your file*):```
tar xvzf NameOfFile.tar.gz
```
This will extract all the files from the compressed archive into your current directory. As for installing these files, it pretty much depends on what you are trying to install (since there are multiple ways of doing it). If this is a source installation, then you will need to use the **make** and **sudo make install** commands, but if it is a binary install then you will probably see an executable file called **install**, **install.sh** or something close to that. It is highly likely that your install is a binary installation... and if it isn't then I highly suggest getting more familiar with installing from source before using the make command.

The only correct way to install these programs is to read the install file that is sure to be included in the package, which would be called **INSTALL**. This is a text file that you can read by doing this (in the directory where the file is located):```
more INSTALL
```

---

### Post by Efwis on 2006-01-04
[QUOTE=PumpkinSonnema]Hi there,
   I'm new to Ubuntu.  Love it so far.  I have a winmodem so whenever I'm connected, I'm in Windows.  
[/QUOTE]

depending on your winmodem you have, you can get a driver for it. this way you don't have to worry about booting between windows and Linux for programs you want.

if yoiu have a conexant chipset, you can get the free driver, granted it connects up slow at 14,400 but at least it's a connection. 

conexent is the only one I know of that charges for fully operable driver for your system. if you pay the $15 USD they will send you the code that allows it to fax and also get the full connection speed like you do in Windows.

other manufacturers, not all, have opened their code up to the linux community. something worth checking out if you are serious about wanting to download and install programs or updates to linux.

[http://linmodems.org/](http://linmodems.org/) this site will help you determine what modem you have and where/how to get the driver for it.

---

