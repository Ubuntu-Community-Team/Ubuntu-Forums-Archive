---
title: "root, sudo, high blood pressure"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by jbeiter on 2006-08-22
Loooong time Unix and Linux admin.. first time I've tried Ubuntu (wanted to find out what the raving is about)

before I give up on this distro, I figured I would come here first. This "no root" environment is really really annoying. It wouldn't be, if sudo -i actually worked for everything but it doesn't.

I get perm errors when I try to install packages, there is no gcc to be found (!?!?!)and every time I try to fix something I get permission errors (sudo -i not withstanding)

apt-get install foo spawns errors.. aptitude barfs when I try to get packages, complaining about not being in the sudoers file.. can't edit the file because I'm not root.

so what am I doing wrong here folks? It must be me or this website wouldn't be here. How does a seasoned sysadmin do something as innanely simple as downloadning a tarball and compiling a game for my kid?

This is the latest ubuntu desktop distro.

Thank you for enduring my rant.
](*,)

should I be booting off CD, mounting the file system and zeroing out the root password? Surely it can't be that simple, and that purposely incredibly annoying..

---

### Post by John.Michael.Kane on 2006-08-22
[COLOR="Red"]**If you want to run as Root you do so at your own Risk**[/COLOR] 

click the link,and it will explain how to turn on the root account.

[**[COLOR="DarkRed"]RootSudo[/COLOR]**]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Kilz on 2006-08-22
It just takes time to gwet used to sudo, and gksudo for graphical applications. Like gksudo gedit /path/to/filename
I think the people with the most problems with it are those who are so used to signing in as root. Since Ubuntu is targeted at new linux users, I wouldnt even waht to think about all the newbies doing that.

---

### Post by enopepsoo on 2006-08-22
you can do 
```
sudo bash
```
to get a root bash.

It sounds like you probably already know this, though.  SOrry for wasting every ones time!
:-({|= :tongue:

---

