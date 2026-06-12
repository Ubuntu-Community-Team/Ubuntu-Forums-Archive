---
title: "Linux....Ubuntu....Debian????????"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Shichao on 2007-04-10
What is the big difference between Debian, Linux, and Ubuntu? Help!!!!!!! When I'm installing programs should I click Linux or Debian for Ubuntu?:confused: :confused: :( :confused: :confused:

---

### Post by Motoxrdude on 2007-04-10
Well, debian is a distro of linux/GNU, and ubuntu is based on debian.
So debian and ubuntu programs will work in ubuntu.

---

### Post by FM1 on 2007-04-10
Linux is the kernel. Debian and Ubuntu are both Linux distributions that run on the Linux kernel. Ubuntu is based upon Debian, but is not exactly the same. If you are trying to install something and there is a package specifically built for Ubuntu, it's probably best to use that. If there isn't, a Debian package may work, but it may not. If whatever you want to install just says it's for "Linux", it's probably a tar.gz that contains the source code, and you'd need to compile that.

---

### Post by PowerPLay on 2007-04-10
LOL.

In my expierience Linux is a type of OS, Debian is a type of linux, and Ubuntu is a redone version of debian. Make sence. If they have a perticualr download for Ubuntu use that, if they have a debian installer grab it and use the pakage installer to instal it. 

-PP(TM)

---

### Post by dstew on 2007-04-10
This explains everything:

[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)

Linux is an operating system kernel, just the skeleton that makes the computer run. Debian is a method of packaging applications, so they are easy to install. A Debian system has its system folders set up a bit differently than a Red Hat system, so Red Hat software packages do not install properly on Debian systems, and vice versa.

Ubuntu is a Linux Debian distribution. It is a package of the Kernel, installed in a Debian way, with a bunch of applications and a desktop environment, meant to be easily installed. There are over 300 different kinds of Linux distributions. See the web site above.

---

### Post by markusfarkus on 2007-04-10
Ubuntu is based off of Debian (or at least that is how it started) and there are a lot of similarities.  While they both have a Linux Kernel Ubuntu and Debian are their own flavors of Linux.  So if you have a choice I would always choose Ubuntu.  However, you will find most of the programs you will need by using the either aptitude or synaptic package manager.  

If you open a terminal you can type in aptitude search %program name% and it will give you the name of the program.  So for instance aptitude search last.  This would search any program revolving around the word last.  I was looking for the gui program for the website last.fm.  I will see one return is lastfm.  To install I type sudo aptitude install lastfm.  I can do the same thing under system administration synaptic package manager.  

As I said most of the packages you need can be found there.  If you need more programs you can quickly do a search on how to edit sources.list to enable more repositories.

---

### Post by KIAaze on 2007-04-10
First, concerning the practical question:
-If you can find an "ubuntu package" in the ubuntu repositories, use it.
-If you find a debian package (.deb), you can also use it. (I think ubuntu packages are also .deb packages, altough I'm not sure)
-If you find a ".tar.gz", it's the source code and it can be installed on any GNU/Linux system. :) (even Windows sometimes)
-Other packages like ".rpm" can also be used on Ubuntu thanks to a conversion program called "alien". ;)

So basically, you're free to choose. It's just more or less easy and time-consuming.
The options listed above are listed in increasing "difficulty" level. (but once you did it once, every option is quite easy, except maybe for the installation from source where you might sometimes encounter difficulties)
The easiest is always to install with the synaptics package manager first.

For the question about the differences:
This little map should make it clear:
[IMG]http://photos1.blogger.com/blogger/3370/2500/1600/GNULinuxupdatedw4.0.jpg[/IMG]

GNU/Linux->Debian->Ubuntu
(father->son)

By the way, Linux is in fact just the kernel of the OS.
All the basic programs and commands running on it are what makes up GNU.
Together, they form the complete OS: GNU/Linux.

More about that distinction here:
[http://www.gnu.org/gnu/gnu-linux-faq.html]("http://www.gnu.org/gnu/gnu-linux-faq.html")
[http://www.gnu.org/gnu/gnu-users-never-heard-of-gnu.html]("http://www.gnu.org/gnu/gnu-users-never-heard-of-gnu.html")

---

