---
title: "[SOLVED] Visual Effects Issues"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Tom11235 on 2008-03-02
Hey,
I am a new user to Linux and Ubuntu.I have been able to install all restricted drivers and have a functioning computer, but cannot get the visual effects to work. I have browsed the forums and have noticed another user with the exact same issue: "The Composite Extension is not available" comes up whenever I try to change the visual effects. I saw a solution on is thread which read as follows:

"change session during login to xclient

install the following package through terminal:

sudo apt-get install x-server-xgl "

I did not try to change the session yet, however, when I tried to install the package it of course asked for the password, but I was not able to type it in. None of my keys worked for some reason! I went to terminal, typed in 
sudo apt-get install x-server-xgl hit "enter" and then tried to type in my password but could not. Does anyone know why this is or how I could resolve this?

Thanks ahead of time.

---

### Post by TeoBigusGeekus on 2008-03-02
If this is what I think it is:
Whenever you type your password after a sudo command, none of the characters are printed on screen, not even asterisks or something.
Just type it (i.e. hit the keys in the correct order) and you are done.

---

### Post by owbizi on 2008-03-02
And press enter. Don't forget to. :)

---

### Post by Tom11235 on 2008-03-02
This is a copy of what I wrote and received from the terminal:


noel@noel-laptop:~$ sudo apt-get install x-server-xgl
[sudo] password for noel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x-server-xgl
noel@noel-laptop:~$ 
noel@noel-laptop:~$ 



What can I do to resolve this?

---

### Post by Tom11235 on 2008-03-02
Nevermind, I logged in using Xclient, and tried it again. It did NOT work, but I did realize there was a typo. I corrected it and received the following:

noel@noel-laptop:~$ sudo apt-get install x-server-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x-server-xgl
noel@noel-laptop:~$ sudo apt-get install x-server xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package x-server
noel@noel-laptop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1843kB of archives.
After unpacking 4854kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libglitz1 0.5.6-1 [76.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libglitz-glx1 0.5.6-1 [29.6kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe xserver-xgl 1:1.1.99.1~git20070727-0ubuntu3 [1737kB]
Fetched 1843kB in 5s (327kB/s)        
Selecting previously deselected package libglitz1.
(Reading database ... 89029 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
noel@noel-laptop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
noel@noel-laptop:~$ 


I am going to try to adjust visual settings from here. If it does not work then I am going to log in using gnome rather than xclient. If that doesn't work then I'll ask for advice and search the forums again.

---

### Post by Tom11235 on 2008-03-02
Turns out I've been running Ubuntu under Xclient so far, now that its under gnome it works great. All extras function. Thanks for the help.

---

### Post by TeoBigusGeekus on 2008-03-02
Brilliant...
Don't forget to mark the thread as solved.

---

