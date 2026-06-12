---
title: "Ubuntu in the window of a shop..."
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kunal_nba on 2006-11-18
Hi, I installed ubuntu in a computer I'm going to put in the window of my shop. The thing is that I need to display a powerpoint presentation in fullscreen everytime I boot my computer, and it has to be automatic.

So I think I first need to login to gnome without typing a password.. like autologin.. and then to add a powerpoint presentation in fullscreen mode to the startup...

Before we had MS Windows in the computer, but I got tired of reinstalling the system all the time.. so I wanna swith to ubuntu as I got good results in my home computer, but I don't know how to setup this..

Can anyone guide me in these 2 steps??..

Thanks..

---

### Post by faraazs on 2006-11-18
You can have the system automatically log a user in by going to System | Administration | Login Window | Security (tab) | Enable automatic login

You can add a startup script to launch powerpoint with the select file as well. I am not sure about making it use presentation mode automatically though its probably just another flag in the powerpoint launch command.

---

### Post by AAM on 2006-11-18
I had a quick look around the Ubuntu system, **kunal_nba**.

The log in changes can be made in *System|Administration|Log* In Window.

The start up for the presentation can be added to *System|Preferences|Sessions*. You will have to look around some more to discover how to have the slideshow start up automatically. You could add the pages into a screen saver too.

I hope this is useful as a start.

---

### Post by adwait on 2006-11-18
Well, I am on Kubuntu so I am not very sure how do the login part with Ubuntu. But somewhere in System Administration, you should find the GDM Manager or something like that. In that, you can setup the system to log in to a particular account automatically. After that, use
```
gedit .bashrc
```

In this file, at the end type
```
openoffice -show <presentation name>
```

This will do what you want. But the presentation MUST be in open office format, ie: odp, it doesnt work with ppt.

EDIT: You can enter this command in the sessions window as well, like they have mentioned in the posts above me.

---

