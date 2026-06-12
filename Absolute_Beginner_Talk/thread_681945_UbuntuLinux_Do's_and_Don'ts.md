---
title: "Ubuntu/Linux Do's and Don'ts"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by davesbrain on 2008-01-29
Hello again.   I just had some general questions for the group.
First, I was wondering what is recommended for a 'fairly' new installation.  I have already done some performance tweaks from sources found here and around the web(except for the filesystem tweak..that one scares me).  I've also done the Firefox (about:config) tweaks.
Is there more that could/should be done?  For security? Stability? 

Also, what should us noobs never, ever, under any circumstance do?


And on a side note:  I'm a bit confused with the booting options.  The whole "run client scripts", "Gnome", "Gnome failsafe"...etc.   And from my understanding, ctrl+alt+F1 closes the graphical interface for a pure 'prompt' environment and ctrl+alt+backspace 'restarts' the OS without actually rebooting the machine.

---

### Post by Ardrias on 2008-01-29
CTRL+ALT+1-6 switches to a terminal without a GUI. Pressing CTRL+ALT+7 takes you back to GUI. In the case of running Compiz and what not, it may have some problems switching back from a non-GUI terminal.

CTRL+ALT+BACKSPACE restarts the X-server, your graphical interface, not actually the whole OS.

---

### Post by emarkd on 2008-01-29
Be very, very careful any time you use sudo to do anything.  And be even more extra careful doing 'sudo rm' anything.  You can mess up really quickly with that one.

<ctrl><alt>F1-F6 shows you some of the non-graphical terminals already running.  You can go there and then get back to gnome(the gui) by hitting <ctrl><alt>F7.

<ctrl><alt><backspace> restarts the x-server.  The gui on linux is actually networked.  The X server runs in the background and your client connects to it.  It doesn't restart anything except the GUI.

There's plenty more but that's the first things that come to mind....

---

### Post by emarkd on 2008-01-29
There's a good notice about dangerous commands at the top of the forum in blue.  It's definitely worth reading.

---

### Post by mb184 on 2008-01-29
You may want to download Automatix ([http://www.getautomatix.com/](http://www.getautomatix.com/)) which will help you aquire a bunch of drivers for multimedia and programs.  Also the easiest way to install and uninstall stuff is through Synaptic Manager.

---

### Post by billgoldberg on 2008-01-29
Take a look at [this post]("http://ubuntuforums.org/showthread.php?t=613462"). Some really usefull things that program can do.

---

### Post by The Cog on 2008-01-29
You will find that you cannot modify files or folders outside your home directory without using sudo ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)).

**Never** try to change the ownership of files (or a hundred times worse, folders) to your personal ownership just so you can do things without using sudo. At best it's a security risk, at worst you will have to reinstall Linux before you can log in again. And you won't get any sympathy from me.

---

### Post by dstew on 2008-01-29
Never EVER give up ;-)

---

### Post by davesbrain on 2008-01-29
Thanx for the tips folks.  I am getting the hang of this.   But even for a seasoned puter vet, a lot of Linux isn't very user friendly.   I do like the whole synaptic thing.  Seems more efficient to check and uncheck what you want and don't want, hit apply.....bam done.   I even got VMware to boot up my XP thats installed on another hard drive.   Compiz is running great and I even put in some extra plugins as described in this tutorial:
[http://ubuntuforums.org/showthread.php?t=659282&highlight=installing+compiz+plugins]("http://ubuntuforums.org/showthread.php?t=659282&highlight=installing+compiz+plugins")
I do have some screengrabs in the gallery under davesbrain

---

### Post by macogw on 2008-01-29
> **mb184 said:**
> You may want to download Automatix ([http://www.getautomatix.com/](http://www.getautomatix.com/)) which will help you aquire a bunch of drivers for multimedia and programs.  Also the easiest way to install and uninstall stuff is through Synaptic Manager.

This would be a "don't"!  Check my sig for details.

---

### Post by mb184 on 2008-01-29
> **macogw said:**
> This would be a "don't"!  Check my sig for details.

Thank you for correcting me in my error, after reading you sig, i am prone to agree that automatix is a dangerous thing

---

### Post by Joeb454 on 2008-01-29
I was just about to post saying I'd avoid Automatix at all costs :) See I was beaten to it some time ago. I've heard some people use it with no issues...but still ;)

---

### Post by aysiu on 2008-01-29
Dangerous or not, these days it appears more difficult to *install* Automatix than it is to install what Automatix helps you install:
[http://ubuntuforums.org/showthread.php?t=645335&highlight=tango+automatix](http://ubuntuforums.org/showthread.php?t=645335&highlight=tango+automatix)
[http://ubuntuforums.org/showthread.php?t=672230&highlight=tango+automatix](http://ubuntuforums.org/showthread.php?t=672230&highlight=tango+automatix)
[http://ubuntuforums.org/showthread.php?t=659034&highlight=tango+automatix](http://ubuntuforums.org/showthread.php?t=659034&highlight=tango+automatix)
[http://ubuntuforums.org/showthread.php?t=321664&highlight=tango+automatix](http://ubuntuforums.org/showthread.php?t=321664&highlight=tango+automatix)
[http://ubuntuforums.org/showthread.php?t=637319&highlight=tango+automatix](http://ubuntuforums.org/showthread.php?t=637319&highlight=tango+automatix)
[http://ubuntuforums.org/showthread.php?t=617962&highlight=tango+automatix](http://ubuntuforums.org/showthread.php?t=617962&highlight=tango+automatix)

---

### Post by erfahren on 2008-01-29
DO: make a habit out of backing up system files before editing them

Also: if you decide to try to write your own little scripts to move files around or what-have-you create another user account with a "fake" directory structure in its home and test them there (thats from experience - lol)

note: I've read that Ctrl+Alt+Del isn't the best way to restart X - it doesn't stop all the services propery so it's more for when it can't be done other ways (maybe someone else knows more about it). 
anyway, see this: [http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

you can also [bind the Ctrl+Alt+Del keys](http://ubuntuforums.org/showpost.php?p=4227702&postcount=2) to open the gnome system monitor to make it easier to kill offending processes if needed 

there are other good tips on the wikis (there seems to be more in the Feisty one, but are probably still applicable):
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Shazaam on 2008-01-29
DO remember that linux is NOT Windows.....

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

DON'T give up :)

---

