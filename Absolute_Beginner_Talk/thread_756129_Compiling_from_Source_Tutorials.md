---
title: "Compiling from Source Tutorials?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by lil0tik on 2008-04-15
Can anyone point me to some good tutorials (or even books) that deal with compiling & installing software from source code?  Also, the 'nix directory structure is still confusing to me, especially when it comes to things like manually installing software...  I'm very used to the major parts of an app being contained in the same directory, as in Win/DOS.  A good, thorough primer on how exactly the directory structure is set up would be a treat too...

I'm pretty new to Ubuntu, but am comfortable using the command line (having spent many a year using M$-DOS) and am motivated to learn more, 'cause Ubuntu's glorious hack-ability is very good at making me feel too-dependent on Gnome.  Please send some links!

Oh, and thanks all - you've helped me build a stable Linux system & I appreciate everything I've learned here.  Now I just gotta learn how to use it better.  :)

-p.

---

### Post by TeoBigusGeekus on 2008-04-15
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
There is a section about installing a source package.

---

### Post by bumanie on 2008-04-15
Look at this guide [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bodhi.zazen on 2008-04-15
Install build-essential and checkinstall

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)

```
sudo apt-get install build-essential
```

Using apt-get (Ubuntu source code form repositories):

```
sudo apt-get build-dep <application> # Installs dependencies needed to compile an application.
sudo apt-get source <application>    # Download application's source code to current directory.
```

Then 
```
./configure && make && sudo checkinstall -D
```

Install from 3rd party [Outside of Ubuntu repos]:

First download the source code and install dependencies, dependencies wither via apt-get or finding and compiling source code.

Unpackage (tar or archive manager).

Open a terminal, cd into the package directory.

Now, 

[list=number][*]Read the README and/or INSTALL file.```
gedit README
```
[*]List the options: ```
./configure --help | less
```You may scroll through the output with up and down arrows, page up, page down ... 
Type q to exit less.


[*]./configure --prefix=/usr # there are two dashes ( - - ) in --prefix (not -prefix)
[*]make
[*]sudo checkinstall -D[/list]

---

### Post by lil0tik on 2008-04-15
a million thanx to everyone, esp. bodhi!  I've got some reading to do :D

---

