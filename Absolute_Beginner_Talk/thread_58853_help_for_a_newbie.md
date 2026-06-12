---
title: "help for a newbie"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by 137.Nexxus on 2005-08-21
ok im not new to linux per say...but i havent used it in 10 years and so pretty much dont remember much about it. my prom\b is that ive downloaded some rpms i want to install and dont remember even how to. i tried using archive manager but thats obviously the wrong program. can u help me? :>

---

### Post by earobinson on 2005-08-21
man alien (pretty sure that is the command, at work)
ps next time a better subject is a go idea eg Help a newbie install an rpm

---

### Post by jyank on 2005-08-21
You'll need alien as stated to convert it into a .deb file 

Alien should be installed at default, but if its not type this into a terminal

```
sudo apt-get install alien
```

then:

```
sudo alien FILENAME.rpm
```

After that it should have converted the .rpm into a .deb file, so you can type:

```
sudo dpkg -i FILENAME.deb
```

dpkg is the depackaging program for debian files and the -i is to tell it to install it.

Have fun :)

---

### Post by 137.Nexxus on 2005-08-21
what is alien and where do i access it?

---

### Post by jyank on 2005-08-21
Alien is a program to convert RPM files into DEB (debian) files.

As far as I know, alien is command line only, so to access it, you would have to type what I posted above.

There might be a GUI for alien, but I've never searched for it because it's a fairly simple program even in a command line.

---

### Post by 137.Nexxus on 2005-08-22
thanx alot. knowing that i can run all the installers now :>

---

### Post by 137.Nexxus on 2005-08-22
ok one more thing. after doing that i want to ru the application in this case it is mplayer....how do i od that ?
basically what i am trying to do is set up  a dvd codec....maybe im going about it all wrong

---

### Post by Knome_fan on 2005-08-22
[QUOTE=137.Nexxus]ok one more thing. after doing that i want to ru the application in this case it is mplayer....how do i od that ?
basically what i am trying to do is set up  a dvd codec....maybe im going about it all wrong[/QUOTE]

Yes, you are going about it all wrong.
1. Ubuntu uses .debs not rpms. Alien is a tool which allows you to also use rpms if there isn't a Ubuntu package, but it sure isn't the normal way to install things on Ubuntu.
2. To for example install mplayer, do the following:
a) Add the extra repositories as described here:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
b) Now fire up synaptic (you'll find it under System > System Managemen (or something like that, I'm not on an english system right now)), search for mplayer, select it and click apply. That's it. 

Have fun!  :grin:

---

