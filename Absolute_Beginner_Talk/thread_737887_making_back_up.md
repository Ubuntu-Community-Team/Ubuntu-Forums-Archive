---
title: "making back up"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by alpdo on 2008-03-28
hi i have a 2 seagete baracudas 160 GB ... can you help me how back up my files automatically from one hard drive to the other

---

### Post by kpkeerthi on 2008-03-28
So you want to keep an 'exact replica' of the working drive on the other?

---

### Post by alpdo on 2008-03-28
not all of my hard drive just few files

---

### Post by Oldsoldier2003 on 2008-03-28
> **alpdo said:**
> not all of my hard drive just few files

you can make a script to copy the files and add it into your crontab. use cp <source> <dest> if its only a few files, if its a lot you can get fancier with the scripting. If you run into a problem ask, there are lots of people that are willing to help.

If you need help making a crontab see[ here]("http://ubuntujourney.wordpress.com/2008/03/26/cronjobs-for-dummies-command-line-edition/").

---

### Post by eivind on 2008-03-28
I use rsync for backing up. From the command line, you type

rsync -a source/ destination/

eg. rsync -a /media/disk1 /media/disk2

Of course, you have to substitute these with the real disk names.

---

### Post by kpkeerthi on 2008-03-28
[Here]("http://linuxmint.com/forum/viewtopic.php?t=3969") is an excellent newbie friendly how to. 

* Works for ubuntu as linuxmint is based on ubuntu.

---

### Post by alpdo on 2008-03-28
i dont know this scripts work can you please explain more details pls

---

### Post by kpkeerthi on 2008-03-28
> **alpdo said:**
> i dont know this scripts work can you please explain more details pls

Take a look at [QuickStart: Back-up, Restore, & Set-up Ubuntu Quickly and Easily]("http://ubuntuforums.org/showthread.php?t=613462") if you are scared of command lines.

---

### Post by alpdo on 2008-04-16
tanks i have downloaded quick start... but i wont run on my ubuntu box.. i have tried to do it manually but i just end up messing my ubuntu system :(:(:(

---

