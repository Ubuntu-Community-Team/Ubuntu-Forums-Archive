---
title: "install libncurses"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by pbelonza on 2005-09-07
Hello I recently installed ubuntu on my laptop. I tried to install kismet to work with my rt2500 wifi card.
I would like to know how to install libncurses or libcurses.

Thanks

---

### Post by heimo on 2005-09-07
To install libncurses on terminal: ```

sudo apt-get install libncurses4
or
sudo apt-get install libncurses5

```

You can install these packages using Synaptic too.

---

### Post by pbelonza on 2005-09-08
thanks for the reply.
i checked the packages and i saw that libncurses5 is already installed.
i'm wondering is this the one that kismet is looking for? if so why is it not detected when i run ./autoconf ? any ideas?

---

### Post by heimo on 2005-09-08
Actually, maybe what you want to do is enable Universe section, like this:
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

And use Synaptic package manager or 
 ```
sudo apt-get install kismet

``` 
to install kismet?

This version is in universe:
[http://packages.ubuntu.com/hoary/net/kismet](http://packages.ubuntu.com/hoary/net/kismet)

Is this what you want to do? I believe what you're trying to do is install from sources, which may be unneccessary. What instructions are you following?

---

### Post by pbelonza on 2005-09-08
[QUOTE=heimo]Actually, maybe what you want to do is enable Universe section, like this:
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

And use Synaptic package manager or 
 ```
sudo apt-get install kismet

``` 
to install kismet?

This version is in universe:
[http://packages.ubuntu.com/hoary/net/kismet](http://packages.ubuntu.com/hoary/net/kismet)

Is this what you want to do? I believe what you're trying to do is install from sources, which may be unneccessary. What instructions are you following?[/QUOTE]

Thanks, actually this is what i want to do. this is just what i was looking for.
many thanks again and wish me luck.

---

### Post by pbelonza on 2005-09-08
Hello again.
Im using kubuntu and i cant seem to find synaptic anywhere.
any ideas where i can find it?

Thanks

---

### Post by heimo on 2005-09-09
Oh, I believe the equivalent of synaptic (in Gnome/Ubuntu) is called kynaptic (in KDE/Kubuntu). I don't know how much different kynaptic is, hopefully you can figure it out, but if not I'll be glad to assist. It's also possible to do this without synaptic/kynaptic by editing /etc/apt/sources.list to enable universe (just remove # marks from lines which begin with word deb and contain word universe) and install packages using apt-get.

This is basicly how you do that, (however you don't have gedit-text editor installed in kubuntu by default, I believe you can substitute that one with kate or kedit):
[http://www.ubuntuguide.org/#extrarepositories]("http://www.ubuntuguide.org/#extrarepositories")

Some instructions how to use apt-get in case you can't use kynaptic:
[https://wiki.ubuntu.com/AptGetHowto]("https://wiki.ubuntu.com/AptGetHowto")

Don't hesitate to ask any questions. :)

Good luck.

---

### Post by pbelonza on 2005-09-09
Thanks,

I've downloaded the kismet package. Now how do I install it to the system?

---

### Post by heimo on 2005-09-09
[QUOTE=pbelonza]Thanks,

I've downloaded the kismet package. Now how do I install it to the system?[/QUOTE]

I try to be more clear. You don't need to download anything, package manager will do that for you. When you have sources.list file edited to point to repositories, servers which have these packages available, all you need to do is use kynaptic or apt-get to install kismet. (on terminal: sudo apt-get install kismet) This will handle all the dependencies (packages which are required to install this package) automaticly. That's the correct way of installing software - that's the way you most probably want to do it.

Use the ubuntuguides (linked above) instructions to edit /etc/apt/sources.list and then run this on terminal:
 ```
sudo apt-get update && sudo apt-get install kismet
``` 
or alternatively, use kynaptic, search kismet, mark for installation and - at least in synaptic - hit apply to finish install. That's very easy once you get used to it, no need to download anything, just select software and let package manager do all the work for you - that's what it's for. :)

To edit sources.list, you need to open it in text editor using root privileges. What this means: this file is important system file and protected from accidental editing / unauthorized changes. There's many ways to achieve this, one way would be to use terminal. Open terminal, enter: sudo kate /etc/apt/sources.list (I've never used kate, I hope this works fine), edit this file according to instructions on ubuntuguide, or just removing couple # characters from the beginning of those lines that are like "#deb [some text here] universe". This will enable universe repositories, parts of software collection where kismet is.

Then you need to update package lists (software available for your system), in synaptic you would hit one button on the toolbar (refresh). On command line the equivalent is to enter: *sudo apt-get update *Then you can install what ever software is available in those repositories, including kismet, just as said above. :)

Sorry for redundancy, I hope this made it easier to understand.  Good luck, post back. :)

---

