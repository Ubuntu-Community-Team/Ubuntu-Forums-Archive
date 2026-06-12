---
title: "Log onto windows network at work?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by ccheaton on 2007-01-10
Hi, I just installed Edgy and am trying to get onto the network at work with it.  I can browse the networks and see servers.  However, I cannot figure out how to log onto one of the servers.  The environment that I work in requires all of the XP machines to authenticate with a particular server upon startup.  Presumably, this is what allows the machine to function on the network and access the internet.  

Assuming that the server name is *server1 *and my login is *user1 *and password *pass1*, what do I need to do to log into the server with Ubuntu in the same manner that I do with windows?

---

### Post by steve.horsley on 2007-01-10
One way is to tye Ctrl-L in nautilus and enter a URL like this:
smb://DOMAIN;user@1.2.3.4/

Alternatively, I keep a directory full of launchers, one for each of our servers. Each file is a text file with contents like this:
> [Desktop Entry]
Name=Documentation-Server
Type=Application
Exec=nautilus smb://DOMAIN;administrator@1.2.3.4/
Terminal=false

You cannot edit these files by right-clicking in nautilus once they're created because they are launchers, but you can edit them from the command line.

---

### Post by ccheaton on 2007-01-11
Will this prompt for the password or do I have to enter it later?

---

### Post by steve.horsley on 2007-01-11
Either way, it will prompt for a password when you try and connect with nautilus.

---

