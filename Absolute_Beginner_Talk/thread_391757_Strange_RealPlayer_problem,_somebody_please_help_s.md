---
title: "Strange RealPlayer problem, somebody please help so I can use it!"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-23
Heya, first I will run you through what I did.

[www.real.com](www.real.com) and downloaded the linux version of the player.

Sitting on my desktop is RealPlayer10GOLD.bin

Inside Terminal:

```
root@Cams-Linux:~# cd ~/Desktop
root@Cams-Linux:~/Desktop# chmod 755 RealPlayer10GOLD.bin
root@Cams-Linux:~/Desktop# sudo ./RealPlayer10GOLD.bin
Extracting files for RealPlayer installation........................
```

So it started installing. It asked me where I wanted to put the Realplayer folders, so inside File System I created a folder called "real"
```

Welcome to the RealPlayer (10.0.8.805) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...


Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/root/Desktop/RealPlayer]: /real/
```

```
You have selected the following RealPlayer configuration:

Destination:            /real/

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: f

```

It asked me if I wanted to use system wide symbolic links. I do not have a clue what these are, so i say no. It finishes installing, so I click RealPlayer 10 in the Applications to play some music, and:

[IMG]http://i10.tinypic.com/2qdxw5y.png[/IMG]

What's going on? Do I need to change something? Please help.

---

### Post by taurus on 2007-03-23
First of all, you should install it to /opt/RealPlayer instead of to /root.  So, when it asks for a whole path, type

```
/opt/RealPlayer
```

And when it asks if you want the program to create a link to it, say Yes so it will create a link in /usr/bin/realplay so you can run it anytime and anywhere since /usr/bin is in your path.

---

### Post by camz on 2007-03-23
thanks i did it

---

