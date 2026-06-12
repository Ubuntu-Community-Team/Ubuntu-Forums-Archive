---
title: "how to access installed programs?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-04-21
This is a daft question really, that must have a simple answer, but I'm buggered if I can work it out!  
When I install something from Synaptic that doesn't automatically produce a menu item, how do I find it and run the program?  (i.e. what the equivalent of an Windows .exe in Program Files?)

For example I've just installed webmin with mysql support from Synaptic, but I can't find it, nor run it.  I tried installing Debian Menu (in the hope that it would wave a magic wand!) but its done nothing.....

Please help a daft fool](*,)

---

### Post by mostwanted on 2006-04-21
You could first try typing web in the terminal, then press tab twice. That should bring up all commands that start with web. You could also try looking up the package in Synaptic and then check where it installs things (anything that's gone into /usr/bin or /usr/local/bin).

---

### Post by taurus on 2006-04-21
Most programs are installed in /usr/bin and if you want to run it, you can run it from a terminal (or prompt) by clicking Applications -> Accessories -> Terminal.  Then, type the name of the prompt.  Or you can hold down <Atl> while pressing F2.  Then, type in the name of the program...

---

### Post by damianubuntu on 2006-04-21
thanks guys!

as it happens (should anyone wish to know) webmin is (of course - doh-!) a browser tool, so its accessed from http(s)://localhost:10000

---

### Post by Caligula on 2006-04-21
[QUOTE=damianubuntu]This is a daft question really, that must have a simple answer, but I'm buggered if I can work it out!  
When I install something from Synaptic that doesn't automatically produce a menu item, how do I find it and run the program?  (i.e. what the equivalent of an Windows .exe in Program Files?)

For example I've just installed webmin with mysql support from Synaptic, but I can't find it, nor run it.  I tried installing Debian Menu (in the hope that it would wave a magic wand!) but its done nothing.....

Please help a daft fool](*,)[/QUOTE]

you can try "alt F2", then write in the name of the program...
I also wonder where the actuall files are, like program files in windows...:confused:

---

### Post by harisund on 2006-04-21
Generally, every installed Linux application (unless it's a web application like Webmin) has an executable file (a .exe file equivalent) with the same name as the package, and in /usr/bin. 

The first one means that if you installed <name> you can simply type <name> from the terminal (if it's a command line application) or you can press Alt+F2 (the "run" equivalent of Linux) and type <name> 

The fact that the .exe equivalent is in /usr/bin means that it is in your path, and so you needn't explicitly mention the path like ./<name> or /usr/bin/<name>

But if you want to know everything the program installed (in WIndows you would generally look under C:\Program Files.) In Linux, open your terminal, and do "dpkg --listfiles <packagename>" and it will tell you every file that the application installed. 

Of course, you can't do the dpkg thing with programs installed from source.

Caligula, the above is for you :)

Note though, if the program you installed is a library (generally starting from lib) they don't have an executable. And some programs are daemons, which can be configured by editing its' configuration files and then restarting the daemon for the changes to take effect. Typical example: Apache.

---

