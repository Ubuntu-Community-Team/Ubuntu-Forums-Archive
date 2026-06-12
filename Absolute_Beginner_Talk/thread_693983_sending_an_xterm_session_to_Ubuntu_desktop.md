---
title: "sending an xterm session to Ubuntu desktop"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by torgis on 2008-02-11
Firstly, spare me the lectures on the insecurity of using telnet over SSH.  I am not the decision maker in this crazy network config we are using here - I am but a lowly peon forced to use this infrastructure to get my job done. :)

Secondly, let me state that SSH is NOT an option.  For whatever reason, the powers that be have indicated that moving everything and everyone (several hundred UNIX and Linux test beds) to SSH would be too much effort.  

What I am trying to do is relatively simple, I do it all the time from a W32 system running Exceed to various UNIX systems in our lab.  It is, basically, this:

telnet to host1.
export DISPLAY=1.2.3.4:0.0
xterm &

That's it.  With my W32 box, the xterm window pops up in a few seconds.  With my Ubuntu install...no xterm window.  I get "Can't connect to display: 1.2.3.4:0.0".

Any thoughts?  Any advice is greatly appreciated.

Thanks in advance,
-torgis

---

### Post by aJayRoo on 2008-02-12
There are a couple of things to consider with this. Firstly because you are explicitly setting the DISPLAY variable you will probably need to use xhost to allow remote connections from that machine like this:
```
xhost + machine.location
``` and obviously replacing the machine.location part with the ip address or machine name of the machine you wish to allow connections from.
The second thing to check caused me a large amount of pain. I turns out that Gnome will not allow remote connections to the xserver by default. To fix this head to the system menu -> administration -> login window. Then head to the security tab and uncheck the disallow remote connections box. Hopefully that will sort your problem out. Let us know how it goes.

---

### Post by torgis on 2008-03-21
Yep, had the xhost +hostname thing down, but the gnome settings were new to me.

Got it running though, many thanks.

---

