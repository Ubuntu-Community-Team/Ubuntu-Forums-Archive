---
title: "How to install applications without connecting to the Internet?"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by elemental_silver on 2005-09-10
I need to know how to install an application, like prelink, without using Synaptic or any other method of downloading online. I have no problem passing the file from one computer to another via CD, but I have no internet/network access on the computer. Prelinking is my current project, so use it as an example, but I also want to have general instructions that would work with any other application/program.

---

### Post by Wolki on 2005-09-10
[QUOTE=elemental_silver]I need to know how to install an application, like prelink, without using Synaptic or any other method of downloading online. I have no problem passing the file from one computer to another via CD, but I have no internet/network access on the computer.[/QUOTE]

OK, but be prepared that it can be a lot of work.

The basic way of doing it is downloading the right package (packages.ubuntu.com) and copying the file to the ubuntu computer, then execute "sudo dpkg -i <filename>" in that directory. (You can also add this to your right-click menu: [http://www.ubuntuforums.org/showthread.php?t=33584](http://www.ubuntuforums.org/showthread.php?t=33584))

The problem is that you may have to download dependencies. On packages.ubuntu.com, it will display the packeages you will have to have installed. If you don't have them (You can check in synaptic), download and install them.

If you're unlucky, these packages can have dependencies you don't have already and so on. You can get the hoary-extras/kubuntu cds to install additional software/KDE.

---

### Post by elemental_silver on 2005-09-10
> If you're unlucky, these packages can have dependencies you don't have already and so on. You can get the hoary-extras/kubuntu cds to install additional software/KDE.

Where do I get that at?

And thanks for the other information, but if the extras CD has the prelink and other packages, it could make life really easy for me.

---

### Post by mlomker on 2005-09-10
I think you're in a tough spot without a network connection.  Contrary to what the other fellow said, most  of the repository info is not available on CD...at least not from Ubuntu because I just looked to see.

You can download the files one at a time from packages.ubuntu.com but if you don't get all of the dependencies correct then you could be doing a lot of walking and cd burning.

Why cant you network them?  Even if you don't have broadband you should at least find a way to dial up by modem from the Ubuntu box.

---

### Post by poofyhairguy on 2005-09-10
[QUOTE=elemental_silver]I need to know how to install an application, like prelink, without using Synaptic or any other method of downloading online. I have no problem passing the file from one computer to another via CD, but I have no internet/network access on the computer. Prelinking is my current project, so use it as an example, but I also want to have general instructions that would work with any other application/program.[/QUOTE]

You can do one of two things: 

Download all the pacakges and dependancies and install with the 

> sudo dpkg -i name.deb

command:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Or do what I would do with no broadband. Use Debian:

[http://www.debian.org/CD/](http://www.debian.org/CD/)

---

### Post by Wolki on 2005-09-11
[QUOTE=elemental_silver]Where do I get that at?

And thanks for the other information, but if the extras CD has the prelink and other packages, it could make life really easy for me.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=30147&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=30147&page=1&pp=10)

---

### Post by sneax on 2005-09-11
For all the cd's and time you will lose I bet you can better buy a network card - or - a dialup. If you want to install big applications you'll have to do it over night with dialup but it's better then always having to burn and walk around i recon.

---

