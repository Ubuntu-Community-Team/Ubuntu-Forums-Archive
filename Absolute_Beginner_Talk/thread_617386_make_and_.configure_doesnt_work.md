---
title: "make and ./configure doesnt work"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2007-11-19
Hi.
I am trying to install Firefox 2.0.0.9 from a tar gz, since it is not in the current repos, but I want to succeed in installing from tar gz's for the experience and knowledge, anyway.
I try to follow the instructions here:[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
but it doesn't work.
I extract the files into its own folder...I cd to it in terminal...

bob@baracuda:~$ cd '/home/bob/downloads/firefox-2.0.0.9/firefox'
bob@baracuda:~/downloads/firefox-2.0.0.9/firefox$ make
make: *** No targets specified and no makefile found.  Stop.
bob@baracuda:~/downloads/firefox-2.0.0.9/firefox$ ./configure
bash: ./configure: No such file or directory
bob@baracuda:~/downloads/firefox-2.0.0.9/firefox$ make
make: *** No targets specified and no makefile found.  Stop.


What to do next?

Thanks.:confused:

---

### Post by dhobbs on 2007-11-19
Do you have the build-essentials package?  You also need to make sure you have the required 'dev' dependency packages.

Often there will be a readme file or an install text file that will give better instructions for installing from source.  Often you will have to run ./autogen.sh first, that will generate the makefile.  Then you run 'make' and then 'make install'.

These are just general instructions though, you may not need to autogen.sh.

Edit:  I just downloaded the 2.0.0.9 tar.gz file from the mozilla site and it looks like you may want to run './run-mozilla.sh', that looks like the shell script that will set everything up.

---

### Post by tyggna1 on 2007-11-19
yeah, 
```
sudo aptitude install apt-file build-essential cvs subversion
```
is needed before compiling software.   Then, correct me if I'm wrong, you usually need sudo priviledges for make and make install, and sometimes for configure too.   

The proper order, as I learned it was:

```
sudo ./configure
sudo make
sudo make install
```

---

### Post by Paul820 on 2007-11-19
You only need sudo for **make install** as you are installing files in the system folders. ./configure and make are done in the folder that is either on the desktop or in your home folder, and they belong to the person building the program so there is no need for sudo for those.

---

### Post by dhobbs on 2007-11-19
[http://kb.mozillazine.org/Installing_Firefox](http://kb.mozillazine.org/Installing_Firefox)

It appears that you don't need to compile, which is something that I thought was odd about the .tar.gz file downloaded, it already has .so files, etc. That means the object files have already been compiled, you just need to move them to a place that makes them usable.  This can be done by following the directions in that MozillaZine link.

For the source you need to get it from here:
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.9/source/firefox-2.0.0.9-source.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.9/source/firefox-2.0.0.9-source.tar.bz2)

From here you will run the commands that have already been explained
```
./configure
make
sudo make install
```

Have fun.

---

### Post by hyper_ch on 2007-11-19
is there a specific reason for you to need 2.0.9? If not then I wouldn't bother compiling it and to by the repository.

---

### Post by baracuda68 on 2007-11-23
> **hyper_ch said:**
> is there a specific reason for you to need 2.0.9? If not then I wouldn't bother compiling it and to by the repository.

I'm a former Windows user that likes to keep up to date with bug fixes. As a new Linux user, I want to learn how to do the make  ./configure  tar gz way of installing programs the Linux way, since not all programs are in .debs, and no more using exe's.

This is a thing that I want to be comfortable with doing, but haven't succeeded yet- seems there's always a roadblock...missing dependencies etc
I gave up on this and used Ubuntuzilla for firefox, but I still want to learn how to tar gz.

---

### Post by runemaste644 on 2007-11-23
well first run```
ls
``` to see if there is a script called configure
Bash to English:> ls: This tells your command line "Tell me **every last file without a . before it** in the directory i am in!"
./configure: tells your command line "Run a script called configure!"

---

### Post by erginemr on 2007-11-23
> **baracuda68 said:**
> I'm a former Windows user that likes to keep up to date with bug fixes. As a new Linux user, I want to learn how to do the make  ./configure  tar gz way of installing programs the Linux way, since not all programs are in .debs, and no more using exe's.

This is a thing that I want to be comfortable with doing, but haven't succeeded yet- seems there's always a roadblock...missing dependencies etc
I gave up on this and used Ubuntuzilla for firefox, but I still want to learn how to tar gz.

Hello,

I think you should heed dhobbs' advice above, because Firefox and Thunderbird comes with precompiled tar.gz pacages. You just need to extract the package, put it in an appropriate folder, and run it from there.

Actually I did this for Thunderbird. I was fed up with Evolution, but the package in the repositories had problems with the latest version of the lightning add-on (the calendar / scheduler plugin for Thunderbird). So I went to the Mozilla site and downloaded the "precompiled" tar.gz package for it. I have extracted its contents to /usr/local/thunderbird with root permissions, made a symbolic link for the executable under /usr/local/bin, made a shortcut to it under the Gnome menu and I am happy ever since.

However, Firefox is another story. Ubuntu is integrated with Firefox. Many things depend on its existance, including but not limited to Yelp; Gnome help system. Therefore, I believe you should not touch it and keep using version 2.0.0.8 under Ubuntu. Besides, if there were a big security issue for Ubuntu, I am sure Ubuntu developers would not hesitate to issue an update for it.

---

### Post by erginemr on 2007-11-23
The following site:
[http://www.mozilla-europe.org/tr/products/firefox/2.0.0.9/releasenotes/](http://www.mozilla-europe.org/tr/products/firefox/2.0.0.9/releasenotes/)

lists the reasons for the update. As far as I can see, the update only addresses some stability issues under "Windows", not for closing any security holes.

---

### Post by pdlethbridge on 2007-11-23
But that doesn't address the problem, how do you install a tar.gz. I'm having the same problem and as a new user would like to know also. My tar.gz is xsensors-0.60 tar gz

---

### Post by erginemr on 2007-11-24
> **pdlethbridge said:**
> But that doesn't address the problem, how do you install a tar.gz. I'm having the same problem and as a new user would like to know also. My tar.gz is xsensors-0.60 tar gz

Then, please refer to the following tutorial:
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

And to learn Linux command line interface (CLI), you may read:
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

thoroughly, which is a great site as a Linux tutorial to new comers.

---

### Post by erginemr on 2007-11-24
By the way, there is a great Debian package "checkinstall", which inserts the software installed from the source to the apt-get system for easier removal and creates a Debian package alongside, when used during the installation. You may learn more about it by:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

The second link above also explains all installation techniques in Ubuntu in general. I strongly recommend you to read it through.

---

