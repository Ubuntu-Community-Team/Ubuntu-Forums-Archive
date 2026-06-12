---
title: "How 2 search for files?"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-02-14
Hi, I'm trying to solve a hardware problem which require a file called [COLOR="Red"]*.inf[/COLOR] but I don't know where it might be on the Ubuntu OS or maybe the Ubuntu CD.  
So I wanted to try to search for it while in the file manager but I don't seem to be able to find such a function.
Any hints?

---

### Post by mednamot on 2006-02-14
I may be wrong, but isn't a .inf file a windows driver file?

my guess is that wouldn't be on either the OS or the CD, but you'd have to dl it, or use your window disc to get to it

---

### Post by frodon on 2006-02-14
Open a terminal and run : ```
sudo updatedb
locate *.inf
```updatedb may take some times (if you run it for the first time) it create a database where the locate command look into for matching files.

I think that [beagle]("http://beaglewiki.org/Main_Page") do the same thing with a GUI (it should be in the repos)

---

### Post by bazcor on 2006-02-14
Also gnome-search-tool is a good file searcher which should be available from a standard install, it was on mine. Just type 'gnome-search-tool' into the terminal.

---

### Post by jingo811 on 2006-02-14
tnx everyone. gonna bookmark this thread for later use.
**mednamot>>>**
Yes you are perfectly right it is a windows driver.  I'm having some hardware issues with my USB Wireless.  It's a long and ugly story so I'm going to spare y'all, but you might catch my show at Wifi section.
Where I'm gonna make my 2:nd attept at solving the Ndiswrapper mystery :-k

Hmm...seems like the old Wifi section has been split into its various distros.  So my long story can be watched on Hoary-->Networking instead if somebody doesn't have anything better to do :-)

---

