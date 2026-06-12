---
title: "Question about Ubuntu &amp; Dell 700m"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by fndngemo on 2007-03-01
Just installed linux for the first time ever, and am wondering if someone can answer a quick question for me.  I'm brand new to Linux so I have no idea what pretty much anything does.  I've been searching the forums and have fiddled around enough to fix the screen resolution issue.  My question now refers to connecting to the net.  On Ubuntu's "connection manager" (not sure what it's actually called), it shows three connections.  One is named eth1 and I'm pretty sure that's my wireless connection.  One is called eth0 and I would venture a guess to say that's my normal LAN connection.  There's also one called "lo" and I have no idea what this is.  Is there anyway to rename these connections, and can anyone help me understand what "lo" is?  Also, if it's connected to wireless AND plugged into the net, will it default to the faster wired connection?

---

### Post by Bachstelze on 2007-03-01
lo is the looback interface. In a nutshell, the one your system uses when it needs to connect to itself. More info on [Wikipedia](http://en.wikipedia.org/wiki/Loopback). About your second question, if two interfaces are active, the one your computer uses to connect to the net is the one you tell it touse ;)

---

### Post by fndngemo on 2007-03-01
I was messing around with some of the settings for the network, and now for some reason my wireless isn't working.  I went into the settings and deleted everything I had put in there for ESSID and password, then when I went to put it back in it still says the connection is "disconnected".  Anyone have any idea why this is?

---

### Post by Alfdog on 2007-03-01
I'm also a newbie, and have a 700m.  The first thing you need to do is find out what wireless card you have.  As for me I have a Broadcom bcm4306, and I found this guide to be the best.

[http://ubuntuforums.org/showthread.php?t=201902&highlight=4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=4306)

good luck!

---

