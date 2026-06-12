---
title: "Very Basic Breakdown of Instication process"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Tobywuk on 2006-10-25
Hi, Im still struggling with Ubuntu, and installing files, so i thought i would first ask for infomration on the basics!

What diffrent installer types are there? and how do you go about installing the diffrent types? Such as .deb files, binary files, synaptic files etc... When explaining things, such as commands, please explain what the command is actually doing.

Thanks :)

Info on these talked about dependencies would also be cool :)

---

### Post by macdo on 2006-10-25
.deb files are binary files, and synaptic is a front-end that installs .deb files. 

So to install a program, you use the integrated package manager to install it (either synaptic or apt-get on the command line). This downloads the actual program from the repository (think of that as a software storehouse on the internet) and resolves the dependencies (i.e., it also installs the other programs and libraries that you need).

So if you type 
```
apt-get install random_package
```
your system will check to see what other libraries and programs it needs for random_package to work, and installs all of them as well.
If you search for random_package in synaptic and install from there, you're doing exactly the same thing, except that you're using a mouse rather than a keyboard...

Hope that helps,

---

### Post by Tobywuk on 2006-10-26
thankyou

How about if you download the program file from a website on to your hard drive and want to install it from there? what sort of file types are there then? how do you install them? and does it still get the dependencies automatically? or are the contained within the package or is it a manual job to go and find them?

---

### Post by kelnage on 2007-09-18
When it comes to downloading .deb files, once they are downloaded you can run them by just double clicking on them.

If the package you're trying to install has dependencies, it will try to find all the required dependencies from the Internet and install them first. If it can't find them, the install will fail - but usually (in my experience 95% of the time) it will find them as long as you have an Internet connection. If it can't, you can probably solve it yourself by a quick search.

If the download isn't a .deb file, there could be a couple of alternatives:

**.exe**: you would have to install them using [Wine]("http://www.winehq.org/"), another open source program. Wine effectively pretends to be Windows 98, so you can install Windows programs. However they tend to run quite slowly in my experience, so if you can find a "native" Linux version, they are almost always better.

**.rpm**: these are written for a different type of Linux - however they can be installed usually. I believe Ubuntu will automatically install them for you.

**.tar.gz** or **.tar.bzip2**: these are compressed files which usually contain the source code (what programmers write to make programs). To install these you have to compile the source code - however, this can be difficult for newcomers, so I'd search the Ubuntu wiki (or read the readme which should come with in the compressed file) for help if you wish to install these types.

Right, that about covers all the types I can think of. Just ask if you come across any others.

---

