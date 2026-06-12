---
title: "Got more questions"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by saB on 2005-09-03
I installed Ubuntu, and everything is just dandy, however:

How do I install new programs? I'm a complete beginner at Linux, and have managed to use the available programs and stuff, but I'll be damned if I know how to install software downloaded of the Internet. I'm used to Windows' just clicking the exe. Can someone help?

---

### Post by numberexhaust on 2005-09-03
In Ubuntu, installing software is not as easy.  Software comes in what are called "packages".  Some packages, in order to be installed, depend on other packages to be installed (because they need certain functionality to work).  In Ubuntu, as well as Debian (the distro from which Ubuntu originated), there is a handy program called "apt-get".  If you know what the name of the package is you want, simply go to the terminal and type:

```
sudo apt-get update
``` 

```
sudo apt-get install gcc
``` 

In this case, I am installing the package gcc.  Normally, if there is a depedancy that needs to be fixed, apt-get on the command line will tell you.

On the other hand, since you're a beginner, a much easier way of installing software is by using the Synaptic Package Manager, which uses apt-get but lays everything out there visually for you to see.

This can be found under System-Administration-Synaptic Package Manager.

NOTE:  Before you can use either of these two tools, you need to follow the steps under "How do I add extra repositories" at [www.ubuntuguide.org](www.ubuntuguide.org) .

If you want to install third party software that isn't listed under Synaptic, you will need to get the .deb file from whatever website and then, in a terminal, type the following code:

```
sudo dpkg -i package-name
``` 

This will function similarly to apt-get after that stage.

Hope that helps.  Post back if you have any other questions.

---

