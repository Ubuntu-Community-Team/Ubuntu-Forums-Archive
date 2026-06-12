---
title: "Congrats to Ubuntu for painless installation"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by millerk123 on 2006-07-27
I was perpared for problems but installing Ubuntu on a three year old HP went without a hitch. Nice job Ubuntu! I chose the option to wipe the old os and use the whole disk drive so my old HP is now a straight Linux box with no trace of Windows.

I used the disk from Amazon and did the desktop installation. Someday I want to add the server stuff, just to fool around with on a home LAN. Does anyone know if I boot from the DVD again sometime and select the server option, will that add the server files and leave the desktop installation alone? 

Kevin

---

### Post by Clay85 on 2006-07-27
Welcome to Ubuntu. My installation was that easy too (don't you love Linux?).

I've actually seen people put Ubuntu on much much much older computers that you would think were trash, but run fine with Ubuntu.

I'm pretty sure Server likes to have its own hard drive space (it will ask you to reformat the whole drive). I'm pretty sure you can install both on one hard drive, but you'll need two seperate partitions and that's where I'm no help. :-/

Also, Server doesn't have a GUI, so I suggest hanging out with the Desktop for now, until you learn more Command Line Interface stuff. You can use Desktop for everything but a LAMP server, I think. (Don't quote me.)

---

### Post by dolby on 2006-07-27
the ubuntu install imho might be painless but installs many packages i dont wanna use, many services run on startup by default to which my hardware has nothing to do with etc. a painless installation means too much customising afterwards.

---

### Post by Clay85 on 2006-07-29
I also found out that you *can* get a GUI for the server edition.
```

sudo apt-get install ubuntu-desktop

```

...still not answering your question.

---

### Post by Herman on 2006-07-29
Hello, millerk123, 
Glad to read of your excellent install, and well done!
>  used the disk from Amazon and did the desktop installation. Someday I want to add the server stuff, just to fool around with on a home LAN. Does anyone know if I boot from the DVD again sometime and select the server option, will that add the server files and leave the desktop installation alone?   You should already be able to access any Windows Shares by clicking 'Places'->'Network Servers'->'Windows Network'. 

What kind of 'server' did you have in mind? You probably mean you want to add server software to your existing desktop installation? I guess you can do it from DVD? I haven't yet tested any Ubuntu DVDs to know about that. 
What I can say is this, I have had a good experience with installing server software from the internet repositories through Synaptic Package Manager. My favourite server software is 'SSH Server' for my home LAN, and I recommend that for between Linux boxes. For a web-page about that,[* Click Here*]("http://users.bigpond.net.au/hermanzone/p11.htm").

There are some more links about other types of Linux networking at the bottom of that page already linked to.
All the best with it, Regards, Herman :D

---

### Post by 3rdalbum on 2006-07-29
Apt-getting ubuntu-desktop when running the Server edition just turns your Ubuntu into a normal Desktop Ubuntu with a server kernel.

Ubuntu Desktop can run a LAMP server, by apt-getting Apache, MySQL and PHP.

---

