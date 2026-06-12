---
title: "Help!!!!!!!!!!!"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Bablefish on 2007-05-12
I am a absolute beginner not only to Linux but also to Ubuntu. So you can understand why I need an accurate manual. But what is going on here? I installed Ubuntu 7.04 yesterday and have already installed some software on it. Including a Linux version of AVG and nothing I found so far even comes close to what I have seen in any guide. For example when I installed that AVG which by the way was a .deb file I found I did not need to use any command lines in any terminal as it did not even appear. In fact I found it was as easy to install as any Windows program, just double click upon it and once Ubuntu saw it was a deb file I clicked on install and a moment later it was installed. Then there are what are commonly called Tar files. What terminal, where is this terminal. All I get when I try in install any of it is a command box asking me to choose 1 of 4 options. Run in terminal, install, display or cancel. Did anyone even checked that manual BEFORE it was posted?  What I need is some HELP!!!!!!!!!!!!!!!

---

### Post by ruscoe on 2007-05-12
.deb files are package files for Debian, the Linux distribution Ubuntu is based on. As you've found, those are typically very easy to install in Ubuntu.

If you are trying to install something from a tar file, you are probably trying to build it from source and this link will prove useful to you:
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

First be sure to open the terminal and type "sudo apt-get install build-essential", without quotation marks, then hit enter to install the software you'll require to make use of the above instructions.

The terminal can be found through your panel menu under Applications, Accessories and Terminal.

---

### Post by heimo on 2007-05-12
Usual way to install stuff on Ubuntu is to use package manager like Synaptic (System->Administration->Synaptic Package Manager).

---

### Post by Happy_Man on 2007-05-12
The terminal is located in System -->Accessories --> terminal.

---

### Post by jfinkels on 2007-05-12
> **Bablefish said:**
> I am a absolute beginner not only to Linux but also to Ubuntu. So you can understand why I need an accurate manual. But what is going on here? I installed Ubuntu 7.04 yesterday and have already installed some software on it. Including a Linux version of AVG and nothing I found so far even comes close to what I have seen in any guide. For example when I installed that AVG which by the way was a .deb file I found I did not need to use any command lines in any terminal as it did not even appear. In fact I found it was as easy to install as any Windows program, just double click upon it and once Ubuntu saw it was a deb file I clicked on install and a moment later it was installed. Then there are what are commonly called Tar files. What terminal, where is this terminal. All I get when I try in install any of it is a command box asking me to choose 1 of 4 options. Run in terminal, install, display or cancel. Did anyone even checked that manual BEFORE it was posted?  What I need is some HELP!!!!!!!!!!!!!!!

Take a look at this website for some introductory information: [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

There's a section called "where is the terminal", take a look at that.

You're going to have to do some reading before getting accuestomed to Linux systems! Tell us if you need more help after reading through someof the psychocats pages.

EDIT: By the way, you should probably hold off on compiling programs from source if you're a beginner! Stick with the graphical package manager, Synaptic, in "System > Administration > Synaptic Package Manager".

---

