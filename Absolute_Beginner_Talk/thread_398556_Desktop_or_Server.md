---
title: "Desktop or Server?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by henky on 2007-04-01
Hello, I absolutely LOVE ubuntu, Thinking about going back to windows makes me sick lol.
So my question
I've got ubuntu 6.10 desktop, but I initially downloaded ubuntu as the means for setting up a server.
I was wondering, I need this computer for personal use ( school downloading movies etc.) but also as a server.
Now, should I use ubuntu server or desktop?
Why would ubuntu server be better as a server than ubuntu desktop.
Is it faster or something?
Also. When I installed lets say, ubuntu server. Should I install something like XAMP or is apache mysql etc already included?
tnx

(This server is going to be used to download ({large}) files)

---

### Post by stokedfish on 2007-04-01
The server editon has no GUI.

Are you familiar with the commandline?

---

### Post by henky on 2007-04-01
> **stokedfish said:**
> The server editon has no GUI.

Are you familiar with the commandline?

tnx, but.... what's GUI? if you mean the terminal program, well a little, like cd/tar etc commands, but that's about all lol

so what do you think? in this case. should I use desktop or server

---

### Post by teaker1s on 2007-04-01
gui is point and click, you can run a server edition with gui but you would have to manually install it. Or you can install packages to turn your desktop into a server

---

### Post by henky on 2007-04-01
> **teaker1s said:**
> gui is point and click, you can run a server edition with gui but you would have to manually install it. Or you can install packages to turn your desktop into a server

OK, so the ONLY difference between desktop and server is that it hasn't got any GUI, the server version isn't faster (I mean other people can download big files faster)etc?....

also do you mean apache mysql etc by packages? if not where can I get these?

---

### Post by stokedfish on 2007-04-01
GUI = graphical user interface

Servers are not supposed to run with GUIs, simply because it makes no sense and also from a security point of view. Not having a GUI is not the only difference, but one of them. You can, of course, install a desktop environment of your choice with APT, but then you could as well just install the a normal Ubuntu, Xubuntu, Fluxbuntu, Kubuntu, Whateverbuntu desktop edition...

---

### Post by henky on 2007-04-01
> **stokedfish said:**
> GUI = graphical user interface

Servers are not supposed to run with GUIs, simply because it makes no sense and also from a security point of view. Not having a GUI is not the only difference, but one of them. You can, of course, install a desktop environment of your choice with APT, but then you could as well just install the a normal Ubuntu, Xubuntu, Fluxbuntu, Kubuntu, Whateverbuntu desktop edition...

ok tnx, but that's what I meant, Now I've got desktop, If I install xamp...., can people download a 500 mb file just as fast as if I would Use the server version? or would their speed increase...

---

### Post by teaker1s on 2007-04-01
yes, ignoring possible security issues you can have both in one machine, also for instance if you wanted say both kde and gnome desktops -this is possible too.

---

### Post by jvc26 on 2007-04-01
The server is the base install of ubuntu, the system with some of the server things like ssh, apache and the like if you ask them to be installed. It doesnt have a desktop, so no gnome, no kde or whatever, the whole thing is designed to be run headless (i.e. without a monitor) If you want to use your computer as a desktop but also enable people to access it to get at files/store files you need to look into things like samba and the like to share folders.
Il

---

### Post by teaker1s on 2007-04-01
bandwidth and hardware resources affect downloads, so you may want a gui on your server and shut gui down to free up resources when not doing maintainance.
or you could run a headerless system and remotely login over the network

---

### Post by henky on 2007-04-01
ok tnx all, I'll see what I can do:)

---

### Post by 3rdalbum on 2007-04-01
I think I've got a proper answer to your question.

If you've got one person downloading a 500 megabyte file from you, then it will download as fast when you're running Ubuntu Desktop as when you're running Ubuntu Server.

If you've got 10 people downloading files from you, and viewing dynamic web pages with database backends, then everything they do will be faster on Ubuntu Server because you have less overheads of memory and CPU usage.

---

### Post by pppetter on 2007-04-01
If you are going to use this computer as a desktop and a server, and you already got the desktop edition just keep it that way and install apache, php and whatever you want. 

It's a little bit tricky, and you'll have to read up on the subject. The questions arising regarding your server software should go in the Servers & Security subforum. Good Luck!


While we are at it, another difference between the server and desktop edition is the kernel - the server kernel has it's timer set lower than the desktop one - alas it's not suitable to play intensive games for example. I have Counter-Strike server, and I installed the desktop kernel on this server becouse the cs server needs the timer to be set higher. 
The timer controls (in short terms) how often the kernel looks for new input, and on a server it doesn't need to be set very high, but on the desktop this is more of a must - else you would think that your copmuter suck becouse of it's slow responsiveness.
I hope that you understand what I was trying to explain. :)

---

