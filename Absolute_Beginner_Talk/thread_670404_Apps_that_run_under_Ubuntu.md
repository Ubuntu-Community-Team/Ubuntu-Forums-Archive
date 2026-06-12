---
title: "Apps that run under Ubuntu"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Joe Hopkins on 2008-01-17
I am very new to Ubuntu or any other Linux systen.  Does anyone know where I can find a list of applications that run under Ubuntu?   Does an application that runs under any flavor of Linux automatically run on all other Linux systems?  If the answer to this question is "not necessarily", what should I look for in an application to ensure that it will run under Ubuntu?
Thanks...
Joe

---

### Post by Joeb454 on 2008-01-17
try [getdeb.net]("http://www.getdeb.net")

Hope that helps :)

---

### Post by mali2297 on 2008-01-17
The first place to look is the official repositories, use Synaptic. If you aren't  using Ubuntu right now, you can also find the packages [here]("http://packages.ubuntu.com/gutsy/").

---

### Post by a9bejo on 2008-01-22
> **Joe Hopkins said:**
> 
If the answer to this question is "not necessarily", what should I look for in an application to ensure that it will run under Ubuntu?

First: The good thing is that you will most likely never need to search for applications at all!  After you installed Ubuntu on your machine, there is a tool that lets you choose from many thousand different programs.  You simply click on the application you want and the system installs it for you.  There are so many kinds of programs that most people install all their software this way.

If you really need to install a program that is not already part of the Ubuntu/Debian distribution, you will want to look for program packages that end with .deb (Debian Packages).  Think of a .deb file as the setup.exe or setup.msi files you maybe know from Windows.  Sometimes, a .deb files depends on a different .deb file to run probably. In this case, you need to install that too.

> **Joe Hopkins said:**
> 
Does an application that runs under any flavor of Linux automatically run on all other Linux systems?  
Generally speaking: Yes.  

Here is the 'not necessarily' part: Let's say a developer writes a program for a mobile device such as a smart phone. Then, maybe the device uses a completely different type of CPU than the one on your desktop.  Maybe it needs a touchscreen to work probably. In this case, a programmer needs to port the program over to the desktop computer to make it run.

Also, different Linux distributions may use different installers (we call them packaging systems) to make an easy and clean install on your computer.  Ubuntu uses the Debian packaging system, which is very popular. So most applications that run on Linux are also packaged as a Debian Package.

---

