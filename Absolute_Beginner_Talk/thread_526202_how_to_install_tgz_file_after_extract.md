---
title: "how to install tgz file after extract?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by csfeeder on 2007-08-15
after i extract file from tgz...this is what i got...
but how to install?
with terminal?
kinda confuse
[IMG]http://img355.imageshack.us/my.php?image=screenshot1yd3.png[/IMG]

---

### Post by shad0w_walker on 2007-08-15
What program are you trying to install? Various programs have different ways of packing their files. Let us know and we should be able to help out fairly easily.

---

### Post by csfeeder on 2007-08-15
[http://img355.imageshack.us/my.php?image=screenshot1yd3.png](http://img355.imageshack.us/my.php?image=screenshot1yd3.png)
this is what i got...
what should i do?

---

### Post by ThrobbingBrain66 on 2007-08-15
If you're using Feisty, you should check in Synaptic to see if you can install MPD without having to compile source code.  MPD is in the Gutsy repos, so I would assume it's in Feisty as well. Assuming you have universe and multiverse enabled, a simple 'sudo apt-get install mpd' in a terminal (Applications > Accessories > Terminal) will install it for you.

---

### Post by jgoguen on 2007-08-15
If you really want to do it this way instead of installing from repository...read the README file before doing anything.  It's called 'README' for a good reason :)

From a terminal:
```
./configure
make
sudo make install
```If there are no errors, then you're done.

The easier and preferred way, of course, is to install from repository:
```
sudo apt-get install mpd
```

---

### Post by csfeeder on 2007-08-17
i still can't install any software using ./configure
i am trying to install pidgin to my ubuntu v 7.04
this is what happen when i am trying to the code u teach..
it shows configure: error: C compiler cannot create executables
am i doing it wrong?
[[IMG]http://img361.imageshack.us/img361/4715/screenshotkb1.th.png[/IMG]](http://img361.imageshack.us/my.php?image=screenshotkb1.png)
actually i did read the readme file :(
and i failed to install

---

### Post by Steveway on 2007-08-17
You should do what jgoguen said.
sudo apt-get install mpd

---

### Post by raul_ on 2007-08-17
[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Amazona aestiva on 2007-08-17
Try:
```
sudo ./install.sh
```

If doesn't work try:
```
sudo apt-get install kompile
```
This program installs tgz files. To start apps->system tools or type kompile.

---

### Post by jgoguen on 2007-08-17
> **csfeeder said:**
> i still can't install any software using ./configure
i am trying to install pidgin to my ubuntu v 7.04
this is what happen when i am trying to the code u teach..
it shows configure: error: C compiler cannot create executables
am i doing it wrong?
[[IMG]http://img361.imageshack.us/img361/4715/screenshotkb1.th.png[/IMG]]("http://img361.imageshack.us/my.php?image=screenshotkb1.png")
actually i did read the readme file :(
and i failed to install
Did you install the build-essential package?

The pidgin package isn't on feisty (unless the devs have a repo up) but gaim is.  mpd isn't a dependency (in fact it isn't referenced at all) so I'm not sure why you're trying to install mpd when you want to install pidgin...

---

### Post by ThrobbingBrain66 on 2007-08-17
> **csfeeder said:**
> i still can't install any software using ./configure
i am trying to install pidgin to my ubuntu v 7.04
this is what happen when i am trying to the code u teach..
it shows configure: error: C compiler cannot create executables
am i doing it wrong?
[[IMG]http://img361.imageshack.us/img361/4715/screenshotkb1.th.png[/IMG]](http://img361.imageshack.us/my.php?image=screenshotkb1.png)
actually i did read the readme file :(
and i failed to install

To install pidgin, go to [www.getdeb.net](www.getdeb.net)  It has precompiled Feisty deb packages for Pidgin and many other apps.

---

