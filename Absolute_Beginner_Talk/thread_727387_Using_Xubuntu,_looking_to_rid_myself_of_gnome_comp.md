---
title: "Using Xubuntu, looking to rid myself of gnome completely."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-17
I'm looking to entirely rid myself of all gnome dependent programs in the hopes of creating a very low resource using operating system while maintaining the idea of being completely useable in every aspect. I'm wondering if anyone knows of any popular gnome dependant programs I may be using that could just as easily be replaced by indepedant or xfce dependant packages. If anyone knows of a useable web browser that would be great. I currently use epiphany which I know requires that you have firefox installed, but I'm not sure if it uses gnome processes such as gnome-keyring-daemon, gnome-pty-helper, and gnome-vfs-helper. Now, I'm by no means a linux power user, nor do I declair myself highly knowledgable in the aspects of the debian system or Ubuntu for that matter. I don't actually even fully understand what all those processes really even mean other than they have to be running for certain gnome utilities to be able to run. Is there possibly a command I can run to see what programs I have depend on a certain running process? Also, I realize that "System Monitor" which comes with Xubuntu is actually known as gnome-system-monitor. Is there another system monitor I could use that doesn't rely on gnome packages? I'm looking to have an operating system that can do the basics, browse the web, play games, download music, and have neat programs like python and such that are reasons why people use computers in the first place. I'm sorry if this post seems uneducated and disorganized, but if I could come up with a system like this, I'd like to use one of the programs I've heard of that allow you to make your own "version" of xubuntu and such that I can install on any lower end system and have them be useable. Nothing upsets me more than knowing I have a few computers that are old yet could still be fully useable with today's standards. Also, I'm a little drunk so I may have mispelled or failed to explain things as intriquate as they should be. I suppose my lasting question would be... what are some programs that use VERY LITTLE system resources that still get the job done?

---

### Post by Lord Illidan on 2008-03-17
Look into some good console applications.

For example, instead of system monitor, I find that htop does just the ticket, if you just want to look at how your system is running. Ok, it doesn't have the fancy graphs.

---

### Post by whoscheesemine on 2008-03-17
anyone have any other suggestions? I am a fan of the console utilities

---

### Post by tobydeemer on 2008-03-17
I was reading a thread that described building up from a server install. You just install the server version OS (don't select any server modules unless you want them) and then install a desktop. That way you can pick and choose what apps to run, without having all those libs and dependencies installed by default. I don't mean "sudo apt-get install xubuntu-desktop" because that does exactly what you're trying to not do. I mean, install xfce, xfwm4, a login manager and then some utilities. That's a bare bones system that you can build from with whatever apps you want. Does this make sense? I'll try to find that thread around here somewhere...

---

### Post by atoc on 2008-03-17
[http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

---

### Post by whoscheesemine on 2008-03-17
> **atoc said:**
> [http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

uhhh that's just the startx, but thanks anyways


well not startx exactly but i think you get what i mean

in other words you could have ubuntu with xfce

---

