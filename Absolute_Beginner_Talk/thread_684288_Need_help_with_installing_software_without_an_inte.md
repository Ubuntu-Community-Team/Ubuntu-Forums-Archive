---
title: "Need help with installing software without an internet connection."
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Tharkun on 2008-01-31
I've been unable to find this anywhere so I thought I'd ask and hope.

The computer I use GNU/Linux on isn't connected to the internet so whenever someone says blah blah sudo apt-get install in regards to software I'm thinking "it won't work because it's not online" I'm not proficient enough to install from source yet (or get something to install from a .deb package either).  Open System > Administration > Synaptic and search for the missing software to install it, won't work of course so will I have to find all the dependencies and install them by hand if I'm going to install something?

What is the simplest .deb package I can install by hand to gain experience doing so.  Eventually I want to install stuff like abiword or wormux.

---

### Post by oedha on 2008-01-31
from the online computer.......
you have to go to [http://packages.ubuntu.com](http://packages.ubuntu.com)
search your application then pay attention on the dependencies...
because you have to download them too.....

~E~

---

### Post by lsmobrian on 2008-01-31
I couldn't say what the simplest .deb is, but if you need to install additional software, what you might be looking for is sometimes included on the installation disk.  You can also download repositories DVDs if you have access to the internet with another computer

---

### Post by emarkd on 2008-01-31
.deb's install without a problem if they're made for your OS.  The issues you're seeing are due to dependencies.  You could [download a package ]("http://packages.ubuntu.com/gutsy/")from Ubuntu, copy it to your Ubuntu Desktop and double-click it.  It'll either install or complain about dependencies.  If it complains, go and download what it needs and install them first.

By the way, that link I gave you above will list the dependencies for each package, but you'll probably already have a lot of them.

---

### Post by erfahren on 2008-01-31
see this post - it addresses situations like yours: [http://ubuntuforums.org/showpost.php?p=3851343&postcount=7](http://ubuntuforums.org/showpost.php?p=3851343&postcount=7)

---

