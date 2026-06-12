---
title: "[SOLVED] pidgin 2.3.1 install help"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2008-02-15
Hello,

I've read the posts that come recommended when you type a new thread in and the how to install anything guide here
:
[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

and have attempted to install via the ./configure whatchamajigger.  it puts out the following:

steve@steve-desktop:~/Desktop$ cd pidgin-2.3.1
steve@steve-desktop:~/Desktop/pidgin-2.3.1$ ./configure
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
steve@steve-desktop:~/Desktop/pidgin-2.3.1$

How can I install this please?  I looked in synaptic and installed everything there but don't think I have the newest version (wanted for the musictracker plugin, which i don't have)

Thanks.

---

### Post by talsemgeest on 2008-02-15
Ok lets go through the process again. So you have extracted the source code to a folder on your desktop called pidgin-2.3.1?
If so, from the terminal type:
```
cd ~/Desktop/pidgin-2.3.1
./configure
make
sudo make install
```
Tell me how you get on

---

### Post by kr0n1x on 2008-02-15
these how-to are better then a "general" compile-from-source guid:
[http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)
[http://ubuntuforums.org/showthread.php?t=658244](http://ubuntuforums.org/showthread.php?t=658244)

good luck!

ps: also this can help you: [http://developer.pidgin.im/wiki/Installing%20Pidgin#Compiling](http://developer.pidgin.im/wiki/Installing%20Pidgin#Compiling)

---

### Post by LowSky on 2008-02-15
if you dont want to mess with the terminal go here
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

pick your version you need

install all three packages, and now you have the newer veriosn of pidgin

---

### Post by AnLGP on 2008-02-15
It says I have two broken packages on my synaptic and to locate them using the 'Broken' filter.  I looked up the broken filter but can't figure it out?

I tried to download those packages in the last post but they had errors.  I tried the terminal above and it came up with the same error reported in the first post.

found the broken ones and clicked 'apply for reinstallation' as that seemed most fitting and this error popped up:

E: /var/cache/apt/archives/libnspr4-dev_4.6.6-3_i386.deb: trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev

Thanks again

---

### Post by rbprogrammer on 2008-02-15
> **LowSky said:**
> if you dont want to mess with the terminal go here
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

pick your version you need

install all three packages, and now you have the newer veriosn of pidgin

why not just install from synaptic??
```
sudo apt-get install pidgin
```

and then install the plugin from the purple website??

---

### Post by TheBoat on 2008-02-15
I recommend LowSky's suggestion. I ran into problems also, but using the .deb, I was able to successfully install it.

---

### Post by AnLGP on 2008-02-15
I have pidgin installed again but it's the older version, I think.  I tried to install the musictracker plugin and all it said was this:

*** Pidgin 2.0+ is required to build MusicTracker; please make sure you have the
*** Pidgin development files installed. The latest version of Pidgin is always
*** available at [http://pidgin.im/](http://pidgin.im/).

Thanks for getting it back up and running but I'm still at a loss with this plugin

additional edit:

I found this in the INSTALL file in pidgin 2.3.1.  It says:

In order to compile Pidgin you need to have GTK+ 2.0 installed (as
well as the development files!). 

Think that could be it?  I'm running gutsy.  Once again, thanks.  You guys are a big help

FINAL EDIT:

You can get it here:  [http://www.getdeb.net/app/pidgin-musictracker](http://www.getdeb.net/app/pidgin-musictracker)

---

### Post by talsemgeest on 2008-02-15
> **AnLGP said:**
> It says I have two broken packages on my synaptic and to locate them using the 'Broken' filter.  I looked up the broken filter but can't figure it out?

I tried to download those packages in the last post but they had errors.  I tried the terminal above and it came up with the same error reported in the first post.

found the broken ones and clicked 'apply for reinstallation' as that seemed most fitting and this error popped up:

E: /var/cache/apt/archives/libnspr4-dev_4.6.6-3_i386.deb: trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev

Thanks again
In synaptic, go edit>find broken packages. Just in case you ever need to do it again.

---

