---
title: "Allow multiple remote windows sessions"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by dawesy on 2007-01-16
Quick background:  I am a Sysadmin coming from the windows world.  I have worked with Linux and Unix before but mostly at Uni and only ever with the CLI, pretty much as a programming platform and later running an Apache installation.  I am now putting a Linux box into production at work running Subversion and Bugzilla as well as a couple of inhouse web apps.  All of that has gone well and I've even got to brush up on my shell scripting to create some backup and other jobs, as well as fighting with a Dell 2950 to get Ubuntu running.  I am running 6.10 Server, edgy, as I never saw [http://www.ubuntuforums.org/showthread.php?t=286209](http://www.ubuntuforums.org/showthread.php?t=286209) before we started!!!!

Anyway, my issue now is that the guys this server is for would like to be able to use the extra grunnt on the box to run some apps etc as it's well over speced for the web serving it's doing.  First step is to set it up so that users can get a remote session to the box with a GUI.  This is where I'm stuck.  I've done all my admin via CLI using ssh.  I don't even have a desktop installed.  I'm trying to work out what solution will allow me to have as many users as I like (up to 10, but probably only a couple most of the time) run a remote desktop session to the system and run whatever it is they need (the intention is matlab, but that's another hurdle later).  I've searched like crazy and seen talk of VNC, FreeNX and vanilla XDMCP but all the threads are about controlling the console or a single user setup, ideally i'd like to leave the console with no GUI as I'll almost never sit at it and certainly don't want to wast resources to put a window around my command line in the cases I do.

So the question is what server/client setup to use to allow multiple windowed session to my Ubuntu server and where is the info to set it up?  Also consideration for making sure they can't power off the box, aside from a loaded pistol and clear instructions!

Thanks all, I know this is probably a no-brainer but I'm a fish out of water on this one!

---

### Post by dawesy on 2007-01-30
Yikes, figures this would be an easy one.  Hope I'm right as I guess I'm going it alone!!

---

### Post by mangoti on 2007-01-30
I like to use XDMCP sometimes. Inever tried but I guess it can accomodate multiple 
sessions.

Even if you dont want to use X, I think you will have to install it anyway on the box and configure XDMCPwith the graphical tool or edit gdm.conf by hand. You can choose to not launch X by default. I dont have a linux box at hand now, so I cant tell you exactely. Do some research on that.

---

### Post by zukakog on 2007-02-05
Bump

I'd also like to know how to install vnc for remote login to my vanilla edgy server.  And by server, I mean that I used the 6.10 server install disk.  I have no gui.  I don't want a gui running on the server's head, but want one for my admins to use remotely.

---

