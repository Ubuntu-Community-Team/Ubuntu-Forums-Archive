---
title: "Ubuntu program like microsoft onenote"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Jerad on 2007-04-26
Does anyone know if there is a program like microsoft onenote?... i am totally addicted to that program. i would love to have it on my ubuntu desktop computer.

---

### Post by Jerad on 2007-04-26
ps... 

i am brand new user to ubuntu... i became addicted after viewing ubuntu beryl on youtube... i just recently got it working thanks to a good tutorial... i am starting to get to know how to use ubuntu... and hopefully get to know it well enough to change all my computers to ubuntu.... just need to know a few things like...

can you play games on ubuntu, for example can you play the game world of warcraft? or company of heros?



link to tutorial:
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

---

### Post by deadlines on 2007-04-26
Frankly I've never used Microsoft One Note, but you might want to check out Tomboy Notes.  It comes packaged with Feisty under Accessories, and seems to be a very handy little program.  It has plugins to extend the capability, easy linking and creation of notes, etc.  Hope that helps.

In answer to your second post, yes you can play World of Warcraft on Ubuntu, however, you will most likely discover that it's not quite as easy to setup as it would be in Windows.  You can accomplish this by using [Wine]("http://www.winehq.com/").  I'm not sure if Wine is available through the official Ubuntu repositories, so you'll probably need to add the Wine repos to your /etc/apt/sources.list to snag a .deb package for it.

One other alternative is [Cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1"), however, I believe you need to purchase a subscription to their site in order to download a copy.  I've heard good things about Cedega, and it may be easier for you if you're just getting started using *nix.

---

### Post by Jerad on 2007-04-26
thanks for the info... i will look into that... appreciate you taking the time to reply

---

### Post by zenkaon on 2007-04-26
You could always install M$ one-note :) 

First of all, install wine - thats windows emulation. That lets you use most windows applications in Linux.

I think that wine is in the add /remove programs section. If not then open a terminal and type:
sudo apt-get install wine

To install M$ one note, put the cd in your pc and go to the cdrom directory in the terminal, find the install.exe and type:
wine install.exe

This is how you can install all sorts of M$ native apps in Linux, some stuff will work, some won't. Most software firms that develop native M$ apps don't even know what Linux or wine are... check out [www.winehq.com](www.winehq.com) for details and a list of what works.

---

### Post by Jerad on 2007-04-26
i very much like tomboy notes.... it will work perfectly... thanks

---

