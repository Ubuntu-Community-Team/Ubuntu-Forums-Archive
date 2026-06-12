---
title: "Linux commands"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by ottawa on 2007-04-14
Hello,

As a totally Linux Newbie I have read through the documentation, have read a lot of the server guide, have installed the server version of Ubuntu 6.10 and have a nice terminal window in front of me. 
The big question: What now ??

Through searching the web I found lots of info on how to update /etc/apt/sources.list, I was even able to do so (wow what a step) but how to close the file ???, that's missing, and not only that.

I am in need of learning the basic most common commands, as I am coming from "click & go" windows. Working with the commandline (terminal in Linux) is not that big of a challenge, as I liked to work with the commandline, BUT HOW ?

So, coming to the point: Where do I find the most common 7 basic commands to get something going ? An old-style written command manual would be preferred, as I like to read up and practice = Learning by doing. :)

Any hints/help would be very appreciated. Tips about a "handheld" book as well.

ottawa

---

### Post by 23meg on 2007-04-14
[http://www.linuxcommand.org](http://www.linuxcommand.org)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by Maestro23 on 2007-04-14
That file is in a directory that is owned by root "/".  Therefore  you need to use "sudo" before any commands to edit it in a text editor.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> sudo nano /etc/apt/sources.list or gksudo gedit /etc/apt/sources.list

As for command line, you can head down to your local bookstore and find many books on Linux command line.  Also there are tons of sites on the net.  I have provided a couple for you below.

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Welcome and Good luck.:D

---

### Post by r4ik on 2007-04-14
[http://www.dsl.org/cookbook/cookbook_toc.html](http://www.dsl.org/cookbook/cookbook_toc.html)

---

### Post by ottawa on 2007-04-14
Wow,

you guys here are pretty quick. That's great.  :D 

Will check out your info. Thank you very much.

ottawa

---

### Post by zvacet on 2007-04-14
[http://www.oreillynet.com/linux/cmd/]("http://www.oreillynet.com/linux/cmd/")

---

### Post by jdietz on 2007-04-17
This is a good list.  Just FYI I am a beginner Linux guy.  My problem is that I do not know how to FIND help.  Like try ifconfig, a basic command a lot of people will need.  If you type "info ifconfig" you get the entry, but if you just type info and try to navigate, there is no way to "See" ifconfig and know that it exists so you can get some help on it.
Another problem I have is that there is not enough command line stuff in the "Yelp" "System" help file.  (The one you get when you push the "?" icon at the top of the screen).
Because there's not enough on-line help it is a real pain to try and get online with linux when you are offline.
So... How do I contribute to the community and modify these files for inclusion in a future linux release?

---

### Post by SOULRiDER on 2007-04-17
You can allways ask for help in the forums and IRC.

---

### Post by ohioboy757 on 2007-04-17
'man' (manual) is the best source of information usually.

I use 'man -k *infoIneed* '

e.g. 'man -k user' displays mans that pertain to user management and various other tasks.  

Hope this helps.

---

### Post by Jem00 on 2007-04-17
Hey,

There is an aawesome tutorial by Kyral : [Terminal for Beginners]("http://ubuntuforums.org/showthread.php?t=73885") 

I am a Ubuntu newbie myself and this tutorial is helping understand it more.:D :D :D :KS

---

