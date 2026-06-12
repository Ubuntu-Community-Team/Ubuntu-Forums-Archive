---
title: "How do I uninstall Ubuntus &quot;ready-made LAMP server&quot;?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-26
So I already knew how to install LAMP on Desktop with terminal.  But ever since I ditched Dapper for Feisty I wanted to try and install LAMP the GUI Synaptic way.  Which I think is a huge mistake when you compare these 2 install methods.
These are the steps I followed to install **LAMP the GUI Synaptic way**.
> 
1. Open Synaptic Package Manager
2. Select "Edit" -> "Mark Packages by Task"
3. Select "LAMP Server"
4. Click OK
5. Click Apply
6. Wait for Synaptic to download and install the services.

**Selects a ready-made Linux/Apache/MySQL/PHP server.**
[IMG]http://i10.tinypic.com/4vq71gz.png[/IMG]

I want to undo this wronging but Synaptic won't allow me to take away the tick.  Thus I can't see all the individual components that got installed which was some 10-20 of them.

Is there a quick and dirty way to undo this or am I forced to redo this process on an another PC and write down by hand all the 10-20 components.  In order for me to search them one-by-one in Synaptic and then uninstall each.  You see why I'm so desperate for a quick click and tick solution, I don't want to write down that long list of components if I don't have to. 	[-(

---

### Post by az on 2007-07-26
There is no difference between methods of installation - you end up with the same LAMP stack and it works the same way.

I don't know about synaptic, but run taskel from the command line and untick the LAMP option.  It will remove the packages.

sudo tasksel

or you can run

sudo tasksel remove lamp-server

---

### Post by jingo811 on 2007-07-26
.....................
......edited.....
.....................
My mistake my notes tricked me :-P maybe I don't have to uninstall after all.

> sudo tasksel
That word tasksel gives me the creeps.  Last time I used it all GUI Ubuntu programs including GNOME got uninstalled before even asking me, I just made one little tick mistake and then it was like **Format C:\**
I'm gonna have to sacrifice a chicken or something before I use that command once again 	:shock: 	[-o<

---

### Post by jingo811 on 2007-07-26
Eh I think there's no problem anymore nor was there any problem.
I logged in with the wrong mysql command and couldn't use
```
show databases; 
```
so I thought that something was wrong, but I just logged in wrong 	:---) sorry I overthinked the situation again.

---

### Post by jingo811 on 2007-07-27
OK so I'm happy with my LAMP installation.  But I don't like not knowing if I can uninstall what I have installed.
So I went to my parents low priority PC and installed LAMP the GUI Synaptic way. then I did the tasksel command to verify if it was true that it was a way to uninstall Synaptic LAMP.
```
sudo tasksel remove lamp-server
```

This time I have proof.  There's some bad mojo with tasksel it literally uninstalls your entire Ubuntu without asking it just starts removing everything.  At the end I had to do 5-6 Ctrl+C in order to stop it, but by then so much was removed I just simply did a full re-installation of Ubuntu.

[IMG]http://i12.tinypic.com/52awvft.png[/IMG]
[IMG]http://i9.tinypic.com/62fwh8y.png[/IMG]
[IMG]http://i11.tinypic.com/4yeslmr.png[/IMG]
[IMG]http://i12.tinypic.com/4z4nw4y.png[/IMG]




You believe me now, there's definitely some bad mojo going on with **tasksel** :-k

---

### Post by ryoz on 2007-09-11
I got the same damm problem. -> re-installing ubuntu :(

---

### Post by afonic on 2007-09-11
Thats pretty weird. I cannot reproduce in the problem in Vmware. I guess you are sure you are not removing Ubuntu Desktop too. I'd file a bug report if I were you. :)

Just note that even if ALL these packages get removed you don't need to reinstall. Just do a sudo apt-get install ubuntu-desktop and you'll get them back!

---

