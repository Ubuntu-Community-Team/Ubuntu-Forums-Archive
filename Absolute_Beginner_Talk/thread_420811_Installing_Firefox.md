---
title: "Installing Firefox"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Drewski on 2007-04-23
Hi guys and gals!
Newbie to Linux here, in need of your sage advice.

I recently installed Dapper Drake, and found it came with Firefox 1.5. Now I tried using apt-get to get a more recent version, but even after an apt-get update command, the latest version is only 1.5.0.11.

So I headed over to firefox.com and grabbed version 2 in the form of a .tar.gz. I extracted this, and found it contained the directory structure for Firefox. Now I want to overwrite my old version of Firefox (which for some reason I found installed in /usr/lib/firefox), so how do I do that, just copy the new files over the old ones? I didn't see any installation script, although I may have just missed it.

---

### Post by LaurelLynn on 2007-04-24
Dear Drewski,

If you unpacked the archive, inside the directories that it creates, look for a file that ends with¨.deb¨.

For example, if the name is ¨firefox.deb¨ it can be installed by the command (in the right directory):

$ sudo dpkg -i firefox.deb

---

### Post by Drewski on 2007-04-24
Nope, no file ending in .deb, not even in any subdirectories.
All I see is a bunch of directories, a bunch of binaries, a bunch of shared objects, and the odd plain-text file.

---

### Post by matchstich on 2007-04-24
i used this

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by LaurelLynn on 2007-04-24
Try that if your still stuck,  look for a readme file. There should be some text file there with instructions.

If you see the files   ¨configure¨ and ¨makefile¨ in the directory then the other standard install method is:

$ sudo ./configure
$ sudo make install

If there are souce code files you may need to add ¨sudo make all¨ before the install command.

---

### Post by Bachstelze on 2007-04-24
The tarball downloaded from mozilla.com is not source code so trying to compile it makes no sense !

matchstich > where are you stuck ?

---

### Post by LaurelLynn on 2007-04-24
Yea, I would be real suprised if it was source.  I have seen binary releases that are installed with make. It is very uncommon though. Usually something from a single developer.

I´m really suprised Mozilla hasn´t built a full debian package file.

---

### Post by matchstich on 2007-04-24
> **HymnToLife said:**
> The tarball downloaded from mozilla.com is not source code so trying to compile it makes no sense !

matchstich > where are you stuck ?

i am not stuck, i just posted a link to how i got the newest firefox installed on my system.
thought it would help the op get it on their system
thanks

---

### Post by Drewski on 2007-04-24
Ok well the archive does not contain source files, only the directory tree for Firefox itself.

The only thing the readme file says is that if I need help installing or configuring Firefox, it gives me a URL to go to (which is absolutely useless.)
I'm going to try matchstich's link, that seems like the best bet. (Except that I can't install mozilla-mplayer using apt-get, that package doesn't exist??)

It seems like there's a lot involved in simply installing an app. I've noticed this is the case with a lot of Linux programs... why is this? Why can't Mozilla just release a simple install script that will automate everything? It just seems very tedious...

---

### Post by Drewski on 2007-04-24
Alright, it seemed to work, awesome! Thanks everyone!

Just a question...

The graphical interface for the Gnome desktop... where is this information stored? Menu configuration, etc.
Because right now I have two quicklaunch icons for Firefox and Evolution mail. Is there a config file somewhere that has this information?

I only ask because I want to understand the internal workings of Linux, not just "how to do things with the GUI".

---

### Post by matchstich on 2007-04-25
i got mplayer from the package manager.

---

### Post by lluisanunez on 2007-04-25
Quick launch icons work pretty much like in W. 
You can right click them and edit their properties, delete them, or create new ones, on the desktop or the panels.

---

