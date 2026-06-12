---
title: "After apt-get where does the program go?"
date: 2005-06-17
forum: Absolute Beginner Talk
---

### Post by leohart on 2005-06-17
Hello everyone,

I would like to ask: In Windows, when you install something, it tells you during the process (most of the time), the path it would install into.

In Ubuntu, I use either apt-get or Synaptic to get new packages but then where does the just installed programs go?

I ask because some programs after I install it has a shortcut in Gnome Panel, some others don't. Say, I use Synaptic to get Tuxkart. Everything went fine and then when I click on Applications->Games. Hmm, it is not there. What can I do if I am in such situation?

Thanks in advance everyone.

---

### Post by bored2k on 2005-06-17
If you to a terminal window (applications - system - terminal) you can type down the game's name to get. What to do to make a menu entry ? Install SMEG and make one yourself.
[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

Applications usually go to /usr/lib, but you do NOT need to touch anything there.

---

### Post by dissident on 2005-06-18
In Synaptic, right click on whatever you just installed and click "Properties" and then on the "Installed Files" tab.

Using the command line you can look stuff up using the **which**, **whereis**, **find**, and **locate** commands. Type **man name_of_command** so see how each of them work. Hope this helps. ;-)

---

### Post by desdinova on 2005-06-18
the actual program you run typically goes to /usr/bin
 
Unlike Windows, there is a bit more structure to where things go in the filesystem

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by leohart on 2005-06-18
Thanks guys for the quick help. I tried typing the name directly and it works (if the package was installed by Synaptic). Linux directories system is quite *different*, what can I say. 

Reading the Linux's directory structure link that **desdinova** gave me now.

---

