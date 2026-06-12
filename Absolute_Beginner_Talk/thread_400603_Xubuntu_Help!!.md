---
title: "Xubuntu Help!!"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Strev_123 on 2007-04-03
Hi all, I've been wrestling with this for days now and have had no luck. I want an up to date linux distro on my aging pc, specs are PIII 766 128mb RAM and 20gb drive. I'm using ubuntu 5.10 at the mo and decided to try Xbuntu 6.10 because of my specs and it worked a treat. Only thing is eciadsl doesn't work in Xubuntu, when trying to start I get the following message
```
$ bash /usr/bin/eciadsl-config-tk: /usr/bin/wish: Bad interpreter: No such file or directory
```
I've read somewhere that you need to install the tk8.3 package and edit shell scripts to point to bash and not sh. All of this is completely outside my knowledge of linux and downloading packages in windows and then transferring to linux doing all the make, configure, install thing, some thing is bound to go wrong. So this is what I thought, unless someone can tell me step by step how to install the tk8.3 package without apt and then edit the shell scripts....

Firstly using the alternate install cd, could I install ubuntu 6.10 with my current specs? All I need it for would be literally boot up configure eciadsl and then use apt to install the xbuntu-desktop package.

Secondly, would the tk8.3 package problem be irrelevant as I assume that this is included in Ubuntu??

Thirdly would getting the xbuntu-desktop package from the Ubuntu 6.10 repo's provide me with Xfce4.4 (as in Xbuntu) or 4.2 as in the Ubuntu 5.10 repo's?

Thanks in advance

---

### Post by Strev_123 on 2007-04-04
Anyone??

Please help :confused:

---

### Post by hyper_ch on 2007-04-04
Xfce 4.4 is available in feisty...

Are you sure you need tk8.3 ? I see in my feisty repos that tk8.4 is also there...
You can install either version (or maybe both) with this command from the command line:
```

sudo aptitude install tk8.3

```
```

sudo aptitude install tk8.4

```
It might well be that you can install only one. I don't know for sure in what repositories. Maybe you have to enable the universe/multiverse one.

And changing the thing in a shell script is quite simple.

The first line of a shell script (normally) states what shell environment shall be used.
In order to make sure that bash is used change (or add) the first line to this:
```

#!/bin/bash

```
But I don't know what what shell script is meant in your question...

---

