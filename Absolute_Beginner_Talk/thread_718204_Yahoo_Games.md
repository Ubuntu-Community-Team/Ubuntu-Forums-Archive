---
title: "Yahoo Games"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2008-03-07
Hi All

I have seen a number of threads of users having issues with Yahoo Games.  Some say install java or check the version of java; others say something about active x controls.  When I attempt to load the games, I typically get the "install java message"

Here is what I for versions

```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
          3    /usr/bin/cacao

Press enter to keep the default[*], or type selection number: 1
Using `/usr/bin/gij-4.2' to provide `java'.
update-alternatives: unable to make /etc/alternatives/java.dpkg-tmp a symlink to /usr/bin/gij-4.2: Permission denied
xoanan@ubuntu:~$ 
xoanan@ubuntu:~$ 

```

Now I also have a screenshot of an attempt to get into yahoo games; I got far enough, but I can't actually type anything.

Any ideas?

---

### Post by Miljet on 2008-03-07
I don't know about Yahoo games, but it sounds like the same problem I had with Pogo games.First open Synaptic Package manager and remove all 3 of the java packages you have installed. 
Go to system -> administration -> software sources and be sure that all extra resources are checked.
Then open a terminal and type:
sudo apt-get install sun-java6-jre sun-java-plugin sun-java-fonts
Reopen Firefox and it should work.

---

### Post by Xoanan on 2008-03-07
10-4, I will give that a whirl and get back with you

---

### Post by pante on 2008-03-07
I´ve learned that Yahoo! is fully functional on Internet Explorer.

---

