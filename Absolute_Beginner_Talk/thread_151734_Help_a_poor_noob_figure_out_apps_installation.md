---
title: "Help a poor noob figure out apps installation"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Mike@castthestorm.com on 2006-03-28
Hey everyone,
I'm a big time noob for ubuntu and Linux in general - but I know a bit of UNIX..
Anyway - I don't know if I understand the whole install process...

I'm trying to install Synergy and I got a "rpm" when I was told to double click - didn't work; it said it didn't recongize the format. Then I tried to get the binaries, platform independent. As I'm told I'm supposed to type:
./configure
make
make install  #of even sudo make install, whatever

The problem is that the terminal doesn't even recongize "./configure" OR "configure".
I already installed the base thing, with the C compilers, that worked because I now have gcc. Am I confused or what? Some help - please?

- Mike

---

### Post by John.Michael.Kane on 2006-03-28
[http://www.newlinuxuser.com/howto-install-an-rpm-package-on-a-debian-box/](http://www.newlinuxuser.com/howto-install-an-rpm-package-on-a-debian-box/)

---

### Post by mostwanted on 2006-03-28
It's also in the Universe repository. If you enable the universe repository (uncomment a few lines in your /etc/apt/sources.listand run sudo apt-get update) you can install it with sudo apt-get install synergy. A totally graphical way to do all this is by using Synaptic which can be found in System > Administration at the top of your screen. Using apt-get or synaptic is the prefered way to install things on Ubuntu you should use that instead.

We should have a general post explaining different methods of installing things...

---

### Post by belikralj on 2006-03-28
The thing with Ubuntu is that it uses .deb packages as in debian while .rpm is Red Hat so you need to use the "alien" command to convert and then install so have a look at the manual pages in the terminal for alien by typing "man alien".

I think this should be your solution.

---

### Post by belikralj on 2006-03-28
I just found this. It should explain a bit more:
[http://www.newlinuxuser.com/howto-install-an-rpm-package-on-a-debian-box/](http://www.newlinuxuser.com/howto-install-an-rpm-package-on-a-debian-box/)

good luck.

---

### Post by belikralj on 2006-03-28
Sorry SD-Plissken   :(   I didn't see the link was the same in your post.

---

### Post by birdman31 on 2006-04-21
So after you install synergy with synaptic, then how do you run it?

---

### Post by DouglasAWh on 2007-09-20
There were a lot of Synergy posts (and threads) in 2006.  I picked this one to re-ignite.  Does anyone know if there's a *.deb for this yet?  I'll figure out the alien thing eventually, but too much SQL, PHP, Javascript, etc. to learn for class...ugh.

---

