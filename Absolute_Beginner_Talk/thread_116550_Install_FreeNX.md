---
title: "Install FreeNX"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-13
Anybody, I need a step-by-step help on how to download and install FreeNX.
I've follwed all links and forums but they all look the same and I can't follow them. I get stuck at the line:

Now we just need to add the following to /etc/apt/sources.lst and apt-get update 

Where do I do this?
I just need somebody to show me a step-by-step process on how to install an run FreeNX succesfully.

:):h34r: Jaygo333 :):h34r:

---

### Post by benplaut on 2006-01-13
[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

^^ the best guide.

When the guide asks you to add something to a certain file, for example /etc/apt/sources.list, type the following command into a terminal:

sudo gedit /path/to/file/given

(for that example, 'sudo gedit /etc/apt/sources.list'), type in your password, and simply copy>paste the lines shown to the end of the file.

sudo apt-get update

^^a command to make the package manager, apt, look at sources.list and make sure it's reading everything on there.

The terminal (command line, shell, prompt... all the same thing) is accessable by going to Applications>Accessories>Terminal... learn to use it, learn to love it, and learn to copy>paste into it - the terminal is great as long as you aren't afraid of it ;)

---

### Post by Jaygo333 on 2006-01-14
Ok, I managed to add those repository adddresses into the list and installed FreeNX. Now what. How do I run it from the localhost to test it and from other pc's. 
Here's the latest response I get from ther terminal

jaygo333@Ubuntu:~$ sudo apt-get install freenx
Reading package lists... Done
Building dependency tree... Done
freenx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://kanotix.com](http://kanotix.com) ./ Packages (/var/lib/apt/lists/kanotix.com_files_debian_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
jaygo333@Ubuntu:~$ sudo nxsetup --setup-nomachine-key
------> You did select no action.
        FreeNX guesses that you want to _install_ the server.
        Type "y" to abort the installation at this point in time.
        "N" is the default and continues installation.
        Use "/usr/sbin/nxsetup --help" to get more detailed help hints.

 Do you want to abort now? [y/N]

I also get stuck at the last line. HELP.1?1

:confused:h34r: Jaygo333 :confused:h34r:

---

