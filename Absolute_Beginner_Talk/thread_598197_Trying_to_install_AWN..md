---
title: "Trying to install AWN."
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jawknee530 on 2007-10-31
I tried following the instructions in [http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981").

I get this error on the final step:

-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libwnck18 (>= 2.15.90) but it is not installable
                              Depends: libawn-bzr (= 0.1.2-bzr78-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libawn-bzr but it is not going to be installed
E: Broken packages

how can i fix this?

---

### Post by macogw on 2007-10-31
try installing libawn-bzr too

---

### Post by jawknee530 on 2007-10-31
i saw that mentioned.  how would i go about doing that?  i got a little in over my head reading through that thread.

---

### Post by Partyboi2 on 2007-10-31
```
sudo apt-get install libawn-bzr
```

---

### Post by jawknee530 on 2007-10-31
i try sudo apt-get insatll libawn-bzr and...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libawn-bzr: Depends: libwnck18 (>= 2.15.90) but it is not installable
E: Broken packages


:(

---

### Post by macogw on 2007-10-31
Looks like that deb is missing from their repo right now.  It's possible that the repo is being updated (it says they update daily from bzr), so it could just be bad timing and something that will work in a few hours.

---

### Post by jawknee530 on 2007-10-31
so the original problem could be casused by them updating or the problem trying to get the fix? also, the first time i tried to add the repos it gave me an error.  i tried again and it went through though.  could that be a sign of a problem?

---

### Post by jawknee530 on 2007-10-31
iiiiiiiiiiiiiiiiiii'm dumb.  i added the repos for feisty and not gutsy.  i tried it again from the beginning and it just installed fine.  now to play around with my new toy.  thank for the help again. :) will it start at boot-up?

---

### Post by macogw on 2007-10-31
ahh ok hah guess that could do it.  if you put avant-window-navigator into your system > pref > sessions > startup it will start when you login

---

### Post by xXMagiciaNXx on 2007-10-31
Hey!It's not that freak hard..

Open a console(again :P) and give the following:


1-Getting the tools: sudo apt-get install build-essential automake1.9 autotools-dev bzr gnome-common libgnome2-common libgnome2-0 libgnome2-dev libgtk2.0-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-vfs-dev libgnome-desktop-2 libgnome-desktop-dev libsexy2 libwnck-common libwnck-dev libxcomposite-dev libxdamage-dev python-gtk2 python-gconf python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev


2-Getting the source:bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator

3-Build and install:
   cd avant-window-navigator/
      ./autogen.sh
      make
      sudo make install


Thats all folks!Should work 100%
Have a nice day :)

---

### Post by macogw on 2007-10-31
> **xXMagiciaNXx said:**
> Hey!It's not that freak hard..

Open a console(again :P) and give the following:


1-Getting the tools: sudo apt-get install build-essential automake1.9 autotools-dev bzr gnome-common libgnome2-common libgnome2-0 libgnome2-dev libgtk2.0-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-vfs-dev libgnome-desktop-2 libgnome-desktop-dev libsexy2 libwnck-common libwnck-dev libxcomposite-dev libxdamage-dev python-gtk2 python-gconf python-dev python-gtk2-dev python-cairo-dev python-gnome2-dev


2-Getting the source:bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator

3-Build and install:
   cd avant-window-navigator/
      ./autogen.sh
      make
      sudo make install


Thats all folks!Should work 100%
Have a nice day :)
er.... it's installed already.  he just put the wrong repos in.

---

### Post by edarroyo on 2007-11-05
Ok, so I tried the steps described by xXMagiciaNXx. Everything went well. I tried to run avant but nothing would pop up. I checked the system monitor for new processes that I didn't see there before, but there were no new ones. Even worst, my Firefox crashes CONSTANTLY now... that didn't  happen right before I installed AWN, so... any tips of what might be wrong? or suggestions to diagnos

---

