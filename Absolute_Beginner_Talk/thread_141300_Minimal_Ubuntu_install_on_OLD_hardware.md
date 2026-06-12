---
title: "Minimal Ubuntu install on OLD hardware"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by fusionrx on 2006-03-08
I have an old Thinkpad 760, 1.2gb HD, 150mhz proc, 96mb ram. 

I'd like to set this laptop up as a small webbrowsing recipe station for the kitchen. Would hook into a home network that is Windows based. Oh yeah, and it would be required to use a Linksys WPC11 wireless PCMCIA card. Don't need any additional stuff like word processing, image editing or all that other fluff... 

Can it be done via Ubuntu???

---

### Post by swamytk on 2006-03-08
1. Go for minimal install in Ubuntu. After that start installing the ligthweight desktop such as openbox(fluxbox), windowmaker, etc. and other necessary applications only.
2. Here is how to on your wireless card: [http://www-scf.usc.edu/~sergior/tutorials/linux-wireless.html](http://www-scf.usc.edu/~sergior/tutorials/linux-wireless.html)

---

### Post by az on 2006-03-08
It should work fine.  Your wireless card should work out of the box.

Firefox will run slow.

Install ubuntu with the server option, log in and edit your sources list to include universe.

sudo vi /etc/apt/sources.list
scroll down to the line with the universe repository in it and press "x" twice to delete the "#" at the beginning of the line and the blank space.   Hit ":wq" and press enter.

sudo apt-get update
sudo apt-get install x-window-system-core menu icewm gdm xterm mozilla-firefox synaptic

And you should be good to go.  The first time you log in graphically, you should change the default session to "icewm" from "gnome" since you do you have most of gnome installed....

---

### Post by IYY on 2006-03-08
Wow, this **is** old... I have no idea why you'd even want to use a box like that for anything other than a firewall. I mean, just recently I bought a 400 MHz machine for $5 on a garage sale!

But... I suppose it will work. I'd suggest Dillo for browsing the web as much as possible (it's very limited and will certainly not work with every single page, but is insanely fast).

---

### Post by meborc on 2006-03-08
more info @ [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

have fun :rolleyes:

---

### Post by fusionrx on 2006-03-09
People ask why on this old laptop? Cause I have it sitting here. Thats why. Cost= free. Win 98 doesn't recongnize wireless card. Why not? Its not like I am using it for anything else. 

I already have 2 other nice computers (Dell XPS Gen2 M170 fully loaded), and a dual processor (dual 866 xeons) dell from a few years back. Plus I am building a new opteron 144 based mATX NF4 6150 system.. I want something I could drop in a kitchen drawer and pull out if I want to look up a recipe, check gmail etc. I don't need a powerhouse for that.

---

### Post by aysiu on 2006-03-09
If it's just to look up a recipe, you don't need Firefox--you can install Dillo or Epiphany.

Have you thought about Damn Small Linux?

---

### Post by meborc on 2006-03-09
i'm running Dapper on old laptop: 336Mhz 128MB RAM 10G HD... full install... gnome... nice themes and icons... and i have no problem using firefox... but i guess it is the RAM that decides that :)

---

