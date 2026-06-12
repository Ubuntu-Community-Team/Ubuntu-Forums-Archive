---
title: "Conceptual Guide to Ubuntu"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-01-31
Has anyone created a conceptual description of Ubuntu(Gutsy)?
What I mean by this is a description on the placement and purpose of things and their layout, where to go to do certain things.

I am coming from the Windows world where I understand where I need to go to do certain things. If I need to adjust settings, I go to Control Panel, or Management Console. If I am looking for Programs I go to my hard drice, then to "Program Files" directory. Etc.

I am having trouble finding things in Ubuntu, simple things, like applications, GParted. Also, I have having trouble understanding what the different directories are for such as "bin", "etc", and others. 

I don't mean to complain. Most things are quite intuitive, but I am finding that there is a fundamental difference in the way the structure or organization if slightly different and I wish there was somewhere I could read about it to bring it all together.

Also, I am wondering what a good backup program would be for Ubuntu. Also, anyone know how to establish a VPN connection, such as PPTP? I have a million questions, maybe i'll get a couple of answers to start with.

Thanks

---

### Post by kpkeerthi on 2008-01-31
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://wiki.ubuntu.com/Training](https://wiki.ubuntu.com/Training)

EDIT: Changed URL to Gutsy's documentation

---

### Post by jordanmthomas on 2008-01-31
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)
[http://www.secguru.com/files/linux_file_structure.jpg](http://www.secguru.com/files/linux_file_structure.jpg)

Why exactly would you need to find gparted?  Typically, you can just run the name of the program and have it run.
```
which gparted
``` will tell you exactly where the binary is and
```
locate something
``` will search your whole filesystem for it.

I'm not very familiar with the other two things you asked, so I'll leave them to someone else.

---

### Post by oedha on 2008-01-31
what if : [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

~E~

---

### Post by onthefence on 2008-01-31
Coming from the world of Windows, you usually click an icon to run a program. Therefore you need to know where the icon is located to run it. If you can't find it you can't run it, although you can search for it.
I tried using the file explorer search function and could not locate it. maybe I was using it incorrectly.

---

### Post by jordanmthomas on 2008-01-31
Nautilus's file search function has never worked well for me.
For example, *.mp3 will find nothing, but .mp3 will.

If you look in Synaptic and right click on a package, you can see what files it has installed.  You can look for any file that has been installed in a /bin directory and that is usually the executable.

Take a look in your /usr/bin, /bin, /sbin, etc folders to see a bunch of things you can run.

---

### Post by onthefence on 2008-01-31
> **jordanmthomas said:**
> Nautilus's file search function has never worked well for me.
For example, *.mp3 will find nothing, but .mp3 will.

If you look in Synaptic and right click on a package, you can see what files it has installed.  You can look for any file that has been installed in a /bin directory and that is usually the executable.

Take a look in your /usr/bin, /bin, /sbin, etc folders to see a bunch of things you can run.

Synaptic???

Thanks, I'll look around there.

---

### Post by kpkeerthi on 2008-01-31
> **onthefence said:**
> Coming from the world of Windows, you usually click an icon to run a program. Therefore you need to know where the icon is located to run it. If you can't find it you can't run it, although you can search for it.
I tried using the file explorer search function and could not locate it. maybe I was using it incorrectly.

Spend some time reading [https://help.ubuntu.com](https://help.ubuntu.com). You'll be glad you did :). Believe me. It will help you know your way around in Ubuntu. The information presented there is not too technical and should be an easy read.
I'm glad that you asked for a conceptual guide... most newbies jump head first and start typing commands found elsewhere in the web not knowing why and what they do, ending up breaking their system soon.
Good luck and have fun.

---

### Post by FrankVdb on 2008-02-02
You're basically asking about two things: how Ubuntu works and how Linux works. You've already received quite a few pointers for the Ubuntu part.

For a general Linux guide, I would recommend the guide written by Machteld Garrels at [http://www.garrels.be](http://www.garrels.be). 

It's one of the first things I read about Linux. Highly informative. There is also a pdf version.

---

