---
title: "Two questions."
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-15
1. How do I configure a program to load on boot? I want the Firestarter and Gaim to start every time I start the computer, but have no idea how to do it...

2. When I download something directly from the internet, not synaptics or apt-get, how do I install the package? usually *.tar.gz.
It really bothers me that I can't install anything I stumble upon on the internet...

Thanks,
Josh:)

---

### Post by fng on 2006-04-15
1. - close all programs
    - start firestarter and gaim again
    - System -> log out
    - mark save current setup
    - log out
    - log back in and both programs will start at login.

---

### Post by jmullagh on 2006-04-15
Josh,,, I think this thread will answer your questions....
[http://ubuntuforums.org/showthread.php?t=153118&highlight=security]("http://ubuntuforums.org/showthread.php?t=153118&highlight=security")

---

### Post by r4ik on 2006-04-15
You could give this one a read,

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Good luck !

---

### Post by Caligula on 2006-04-15
Thanks, I managed to install stuff...

But about the loading at boot thing, I want it to actually load on the boot process, not as part of the session. And also it doesn't work good because firestarter needs to be run as root, so I need to start it again anyway...

The gmail notifier didn't open at all...

---

### Post by user1397 on 2006-04-15
[quote=Caligula]Thanks, I managed to install stuff...

But about the loading at boot thing, I want it to actually load on the boot process, not as part of the session. And also it doesn't work good because firestarter needs to be run as root, so I need to start it again anyway...

The gmail notifier didn't open at all...[/quote]
To do this, got to System>Preferences>Sessions.
In the "Startup Programs" tab, click add and then for the commands:
firestarter: gksudo /usr/sbin/firestarter
gmail notify: gmail-notify
gaim: gaim
Please reply if this worked.

---

### Post by Bloch on 2006-04-15
System --> Preferences --> Sessions 
You can add programs or scripts that start when your session starts.
But a GUI application will always start after the session starts, won't it? It can only start after your desktop environment with your preferences has started.

---

### Post by user1397 on 2006-04-15
[quote=Bloch]System --> Preferences --> Sessions 
You can add programs or scripts that start when your session starts.
But a GUI application will always start after the session starts, won't it? It can only start after your desktop environment with your preferences has started.[/quote]
correct :cool:

---

### Post by Caligula on 2006-04-15
Yes, but that's not what I meant...
I mean that I want it to load as default, not only when I resume my last session.

And I'm using XFce, how do I do it there?

About the installing stuff, I managed to install .deb and .rpm packages, but what do I do with tar.gz?

Thanks

---

### Post by user1397 on 2006-04-15
[quote=Caligula]Yes, but that's not what I meant...
I mean that I want it to load as default, not only when I resume my last session.

And I'm using XFce, how do I do it there?
[/quote]
If you tried my way in gnome, it would load as default, but i'm afraid that I'm not familiar with XFce, so I can't help you further.  You could install ubuntu-desktop from a terminal, by typing sudo apt-get ubuntu-desktop.

---

### Post by Caligula on 2006-04-15
I have Gnome, but I prefer using XFce... if I do it in Gnome, will it load on XFce 
as well?

---

### Post by user1397 on 2006-04-15
[quote=Caligula]I have Gnome, but I prefer using XFce... if I do it in Gnome, will it load on XFce 
as well?[/quote]
I don't really know, but it wouldn't hurt to try :)

---

### Post by user1397 on 2006-04-15
Please reply if it worked or not.

---

### Post by Caligula on 2006-04-15
I didn't really manage to do it, even in gnome.. I don't know the commands for the programs I want to start...

---

### Post by user1397 on 2006-04-15
[quote=Caligula]I didn't really manage to do it, even in gnome.. I don't know the commands for the programs I want to start...[/quote]
I already told you the commands.
They are:
For Firestarter: gksudo /usr/sbin/firestarter
For Gmail Notify: gmail-notify
For Gaim: gaim

---

### Post by Caligula on 2006-04-15
oh, yeah, sorry about that...
And no, it doesn't work with XFce, onlt Gnome...
tough luck...

probably there is some text file to edit...

---

### Post by user1397 on 2006-04-15
[quote=Caligula]oh, yeah, sorry about that...
And no, it doesn't work with XFce, onlt Gnome...
tough luck...

probably there is some text file to edit...[/quote]
Then I suggest using gnome unless your computer is old or you just plain like xfce.

---

### Post by Caligula on 2006-04-16
nah... I'll just turn them on every time I log in...
If that's what it takes to use XFce then alright...  so be it.

---

### Post by Mustard on 2006-04-16
I thought I would take a look over the documentation for XFCE, since I have seen this same question asked before.  You might like to look it over yourself to see if you can gain any insight into how it works..

Info on sessions...
[http://www.xfce.org/documentation/docs-4.2/xfce4-session.html](http://www.xfce.org/documentation/docs-4.2/xfce4-session.html)

Main documentation page..
[http://www.xfce.org/documentation/](http://www.xfce.org/documentation/)

Also, you are going to have some issues with getting firestarter running due to it needing the password to run.  There is a quite lengthy thread on the subject.

[http://www.ubuntuforums.org/showthread.php?t=136934](http://www.ubuntuforums.org/showthread.php?t=136934)

---

