---
title: "installing programs taking long times... strange??"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by intransit on 2007-07-18
Hi All,

I'm new to ubuntu, and for the last couple of days i've been messing around with the ubuntu desktop 7.04 with a few hurdles to get going (changing the 24 bit display, getting the mouse to work again)

Anyway, because I use msn messenger so much, I wanted to start seeing what alternatives I have over on the linux side. So I downloaded pidgin

[http://developer.pidgin.im/wiki/Installing%20Pidgin#Packages](http://developer.pidgin.im/wiki/Installing%20Pidgin#Packages)

anyway, start the process with unpacking

so tar xvzf pkg.tar.gz

./configure 

(which wouldn't work till I downloaded something else, err... here is the info i followed, from that website above)
-------------------
I am on Ubuntu; how do I get $DEPENDENCY installed so I can compile Pidgin? ¶

You need to install the development headers; these are the -dev packages. A simple "apt-get build-dep gaim" will find and install all of the required header packages for you. 
-------------------
which didn't work untill i did apt-get update (pretty sure)

Once that had been done ./configure took about 4-5 mins

Then make took agees like 20-30 mins to complete.

Given I'm running it through Virtual PC with 356 limited ram, (and virtual pcs only limitations)..... why on earth does this take so long? the archive itself (the tar.bz2) was only 7 MB in total. Every thing else i've done so far has seemed relatively fair waiting time, including the install and boot times, which is why I can't understand why it would take so long to do such a simple thing.

I am quite happy with ubuntu so far, this is one of the things which really confuses me

---

### Post by intransit on 2007-07-18
lol, and how do i run it now that make finished?

can't find it anywhere

doing the old windows look on desktop and applications menu, clearly wrong places lol

---

### Post by tgoose on 2007-07-18
That wasn't installing, that was compiling, which means it had to go through the entire source code and convert it to something that can run. There are pre-compiled packages to download which means you don't have to go through with all of that: see [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin) (I have no idea why the screenshot looks like that!)

When compiling, after ./configure you need to run make and sudo make install. That should put t in the applications menu under Internet. If not, running pidgin from the terminal should work. But just downloading the package from getdeb is much easier!

Also, Pidgin is just a newer version of Gaim, which should already be installed. Pidgin will be included in the new version of Ubuntu, but Gaim isn't so bad (although it looks a lot less nice!)

---

### Post by intransit on 2007-07-18
I see

So it took so long on make cos that was compiling

But is that the typical way people install programs? Or do most go to that site you pointed me too?

What to do after make has completed?

---

### Post by tgoose on 2007-07-18
It's only necessary to compile it yourself if either no-one else has done it, or you have some special requirement and need to compile it with some different options. So long as there is a .deb that works, from a trustworthy site (and I've no reason to see anything wrong with getdeb!) then it's quicker and easier to use that. There's no reason not to compile yourself, it just takes longer.

Some people prefer to compile everything themselves because it gives them more control over the system, but I don't really think it's worth it for most people in normal situations.

---

### Post by intransit on 2007-07-18
sorry i see that you changed your post now answers my question

I tried GAIM, but no contacts showed up and it seemed completely unresponsive, so tried this new one

---

### Post by intransit on 2007-07-18
something must've either changed/refreshed

all working in pidgin and had the account i put in GAIM, and all contacts showed up so i'd say it'd probably work in the other one too, maybe I didn't wait long enough or something


How do i put this into like the Applications menu  though?? I'm cluttering my dekstop with crap at the moment

---

### Post by tgoose on 2007-07-18
Generally I'd expect .deb files to put an entry in the Applications menu. Try restarting, and if that doesn't put one in, install alacarte in System -> Administration -> Synaptic

Then go to the terminal, type ```
which pidgin
```

Then go to System -> Preferences -> Main Menu

And add an entry called Pidgin. The path should be whatever ```
which pidgin
``` told you, probably ```
/usr/bin/pidgin
```.

The icon will be /usr/share/icons/hicolor/48x48/apps/pidgin.png or something.

But you shouldn't have to do any of this, because it should have automatically appeared when it was installed! I don't know why it wouldn't have.

It's not a good idea to mess around with the menu editor too much, because it's fairly buggy. That means, no creating hundreds of folders to rearrange everything, I'm afraid!

---

### Post by Hobo Joe on 2007-07-18
If you install things through synaptic, they will be put into the menu automagically. For future reference, becuase I see you already have this installed.

In case you didn't know, it's System > Administration > Synaptic package manager.

It will have most everthing you need to install in Ubuntu.

---

