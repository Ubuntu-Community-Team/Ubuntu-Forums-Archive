---
title: "Pls. need some help"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Doron on 2007-09-22
Hi
I am new with Linux and a very basic user..

a few days ago I installed Ubuntu 7.0.4, but I can't do several things:

1. i can't connect to messenger and icq through Gaim.

2. can't open "Evolution". It simply fail to open

3. How do I see my XP threw Ubuntu, insted of restarting each time to switch OS?

I think, thats all for now...



Thanks

---

### Post by Lord Illidan on 2007-09-22
Do you have internet access for a start, in Ubuntu?

You cannot use XP under Ubuntu, unless you virtualise it..which is rather complicated for a new user.

Regarding Evolution, can you open a terminal (Applications -> Accessories -> Terminal), and type evolution in there? Please copy and paste any output of that  here.

---

### Post by skymera on 2007-09-22
you can see the XP drive, but thats it, unless you really want to virtual it.

whch isnot good.

---

### Post by Doron on 2007-09-22
Thank you..

I do have internet access. I am using Ubuntu now..

This is what was displayed, when I typed "evolution" in the terminal:

(evolution-2.10:8530): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:8530): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
Segmentation fault (core dumped)
doron@doron-Linux:~$

---

### Post by Doron on 2007-09-22
no one knows?

---

### Post by Pumalite on 2007-09-22
Do this at the Terminal:

sudo apt-get update

Post the output.

---

### Post by Jeroen Vernooij on 2007-09-22
Evolutions segfaults, which is why it don't start.

maybe this fixes it: paste this in a terminal:
```
sudo apt-get --reinstall install evolution evolution-common evolution-plugins
```

---

### Post by Doron on 2007-09-22
hi

so I tried both commands in the terminal, but after I type them, it seems it wants a password, but I can't type anything....

---

### Post by Maestro23 on 2007-09-22
> **Doron said:**
> hi

so I tried both commands in the terminal, but after I type them, it seems it wants a password, but I can't type anything....

Type you user password in.  The cursor does not move. HIt Enter.

---

### Post by Doron on 2007-09-22
this is the lay out of the 2 commands.. 

is it ok yo type "yes"?

thanks alot

---

### Post by tcoffeep on 2007-09-22
[Mistake. Nevermind]

---

### Post by Doron on 2007-09-22
sorry..............:-)

doron@doron-Linux:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:2 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty Release
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/restricted Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/universe Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 2s (1B/s)  
Reading package lists... Done
doron@doron-Linux:~$ sudo apt-get --reinstall install evolution evolution-common evolution-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 22.0MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by Jeroen Vernooij on 2007-09-23
after that last command I gave you, 
1) type Y
2) press enter

then evolution will be reinstalled, so maybe it will start again.

---

