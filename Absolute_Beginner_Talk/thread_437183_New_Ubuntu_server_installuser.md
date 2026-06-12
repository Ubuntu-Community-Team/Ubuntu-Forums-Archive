---
title: "New Ubuntu server install/user"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by chris48178 on 2007-05-08
Hello, downloaded and installed Ubuntu server today.

Moving from a Windows 2003R2 Server with PHP/MySQL/Apache. Server was giving me grief, so I looked for an alternative. I have been a windows-only systems admin for 8 years.

This server is only to run a personal web site and learn new skills.

The server appeared to install correctly, and I could log in with the account I created, but I guess I was expecting a GUI. I am out of my element with command line.

I am not even sure where to begin. I have looked through all the docs, but they all seem to be desktop oriented.

Can anyone point me in the right direction to get started?

---

### Post by rgrimes on 2007-05-08
I feel your pain, I'm in the same basic situtation. Hopefully there will be some answers here. I've been looking thru some of the posts and looks like a lot of good info. 
Good luck!

---

### Post by annda on 2007-05-08
you can start here:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

you can also (temporarily) install a GUI on top of the server to speed up the learning process by having a browser and pdf viewer on the same machine as your server:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

you will need to type

```
startx
```

to start the Xserver with the GUI.

---

### Post by chris48178 on 2007-05-08
Cool, that will give me something to start with.

Thx Annda!

---

### Post by christhemonkey on 2007-05-08
You can install a LAMP stack ontop of the desktop edition.
Ubuntu-server is basically normal ubuntu minus all the GUI stuff and a couple of other things and with a different  kernel and things like LAMP included by default.

---

### Post by chris48178 on 2007-05-08
Given that this gets me going...

What would be recommended for FTP access?
What is the best way to access the server from Home? (The server will be installed at a different location)
What is a recommended mail server program? (Pegasus Mail?)

---

