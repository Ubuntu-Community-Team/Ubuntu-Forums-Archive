---
title: "has anyone played worldforge ???"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-18
I've found this game at :
[https://sourceforge.net/project/showfiles.php?group_id=11799](https://sourceforge.net/project/showfiles.php?group_id=11799)
but I have no idea what to download - there are so many files...
and how to install them later...

btw - here are the officual sites :
[http://worldforge.org/](http://worldforge.org/)
[http://worldforgedev.org/](http://worldforgedev.org/)

opensource4ever!!!

---

### Post by u.b.u.n.t.u on 2006-06-18
Here is their forum. They should be better able to answer your questions.
[http://forums.worldforgedev.org/](http://forums.worldforgedev.org/)

Here is an install guide for one of their two demos.
[http://worldforge.org/dev/systems/acorn/install](http://worldforge.org/dev/systems/acorn/install)

-------------

Linux installs are a complete mess in my view. Linux desperately needs the equivalent of Windows exe.

As an example.

The Linux way:

"Installation from CD

Installation of the Acorn client and server is managed by the Loki setup program. To start the installation, run setup.sh from the CD, and follow the on screen instructions.

If you do not have the CD available, the easiest option is to download the CD image from one of the worldforge download sites, and install directly from the image. You can do this either by mounting the image as if it were a CD using loopback, or by using you favorite CD writing software to write the image to a recordable CD.

To mount the image using loopback, create the mount point and mount the image as root as follows:

[root at localhost:~] mkdir /mnt/tmp
[root at localhost:~] mount -t iso9660 -o loop /tmp/acorn-0.4-min.iso /mnt/tmp"


The Windows way:
"Click setup.exe".

I like ubuntu, but all of linux needs to get with the program and make a one click install. They can make it "setup.linux"  So that "linux" is like "exe".

---

### Post by MaximB on 2006-06-18
I am very confused...there are so many files...
I don't know what to download to play games...

help plz...

---

### Post by wog on 2006-06-18
The only things about the worldforge games I've figured out so far is to install sear through the synaptic installer. Sear is the program that lets you connect to the servers in the same way the World of Warcraft program lets you connect to the online servers to play the game.

What I haven't figured out yet is how to get a username and password so I can connect to one or more of those servers online... :(

---

### Post by WhiteHorse on 2006-12-23
Well I got Ember to work by downloading the source, dependencies, and compiling it myself. I can't seem to get the synaptic sear client to work. I keep getting the error:
Sprite compass_case has no filename defined
Sprite compass_needle has no filename defined
Sprite compass_needle_shadow has no filename defined
Error: Varconf Error:
Varconf Error: could not open configuration file "/usr/local/share/sear//data/general.cfg" for input.

Error: Error processing /usr/local/share/sear//data/bindings.cfg
Error:
Varconf Error: could not open configuration file "/usr/local/share/sear//data/states.cfg" for input.

Error: Varconf Error:
Varconf Error: could not open configuration file "/home/jsnod/.sear//general.cfg" for input.

Error: Error processing /home/jsnod/.sear//bindings.cfg
Error: System: Error opening script file: /home/jsnod/.sear/sear-media-0.6//media.script
Unable to set 640 x 480 video: Couldn't find matching GLX visual
Creating window with stencil buffer failed. Trying again without stencil buffer.Unable to set 640 x 480 video: Couldn't find matching GLX visual
Error initialising Sear!
Error: Error initialising Sear. See log files or stdout/stderr for more details

Oh yeah, and glxgears wrks fine and glxinfo says something like "Your system is God" or something like that.... hehe

---

### Post by darkazurka on 2008-05-27
I'm using Hardy Heron, and the package in synaptic is sear version 0.6.3+cvs20080127-1ubuntu1
Thus from January 27 2008. Pretty recent I think.

My experience so far on the server amber has been lots of rectangles (in 3D), my character goes to the right although I press w(as in forward, solved I should have not touched the arrow keys at all) makes me dizzy. 3D: It doesn't seem to take advantage of my 3d acceleration provided by my graphics card.

Now I tried the Xendra server at least here when I press 'w' button it goes forward. Pretty relieved that it works well. Although still 3D rectangles, but they are better than nothing :)

---

