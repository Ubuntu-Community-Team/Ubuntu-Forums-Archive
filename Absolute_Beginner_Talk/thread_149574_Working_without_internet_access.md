---
title: "Working without internet access"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-03-24
Reading posts about getting new apps, the instructions always involve reaching out over the web. Unfortunately my box is, and will remain, offline. I have net access via windows boxen at the library. Can i use these to dl apps from repositories to cd, then dl from cd to my box? How would i do this?

---

### Post by Sef on 2006-03-24
To install offline, read this post:

[http://cargol.net/~ramon/ubuntu-dvd-en]("http://cargol.net/~ramon/ubuntu-dvd-en")

---

### Post by Jussi Kukkonen on 2006-03-24
[QUOTE=gr0kzer0]Reading posts about getting new apps, the instructions always involve reaching out over the web. Unfortunately my box is, and will remain, offline. I have net access via windows boxen at the library. Can i use these to dl apps from repositories to cd, then dl from cd to my box? How would i do this?[/QUOTE]

Sure. Go to [http://packages.ubuntu.com](http://packages.ubuntu.com), find the package you want (remember to search for packages for your Ubuntu version), download the .debs for your architecture. Install with *sudo dpkg -i package.deb*. Uninstall like all other software.

The dependencies are a problem however: This will only work for applications with no extra dependencies, or with dependencies that are simple enough to download by hand... 

I remember reading about a "Extra software CD for Ubuntu" (or something like that), can't remember if it was just a plan or something exisiting -- you should probably try to search for something like that if your needs aren't very special...

---

### Post by gr0kzer0 on 2006-03-24
Thanks everyone. An 'extras' cd is a good idea, ubuntu should do one. There must be lots of users with restricted internet access. Oh, can someone explain how i can get a list of whats on the installation cd? Before i go hunting for apps that i may already have at home

---

