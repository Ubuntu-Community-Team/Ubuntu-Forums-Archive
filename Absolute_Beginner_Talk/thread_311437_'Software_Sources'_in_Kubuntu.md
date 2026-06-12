---
title: "'Software Sources' in Kubuntu ?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by tiptip on 2006-12-02
Hello,

Where is the "System -> Administration -> Software Sources" in Kubuntu ? 
it was easy to find it at ubuntu but i'm checking kubuntu now and i cannot find it.
I know i can use 
```
sudo gedit /etc/apt/sources.list
```
But i'm searching where i can change it inside xwindows.

---

### Post by stupidkid on 2006-12-02
K menu > System > Adept Manager

There's an option in there for managing repositories. Do you have gedit installed? Use kate as a replacement if you don't.

---

### Post by groggyboy on 2006-12-02
you want to manage your repos?

if that is what you want to do, you can use adept (the kde equivalent of synaptic).  Go to Kmenu > System > Adept Manager.  Once your in Adept, go to View > Manage Repositories.

---

### Post by tiptip on 2006-12-02
Thanks, groggyboy & stupidkid
> **stupidkid said:**
> Do you have gedit installed? Use kate as a replacement if you don't.
I noticed 'kate' but since many "HOWTO" are using 'gedit' and it is easy to copy&paste them i installed 'gedit' as well.

---

### Post by aysiu on 2006-12-02
Try ```
kdesu kate /etc/apt/sources.list
``` More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by tiptip on 2006-12-02
Another little question, i'm working by a "howto" [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)   
and the guy there uses a package key for the repositories ,
how i use those keys kubuntu ??

(for the record, i like the look+programs of kde more than gnome :-\" )

---

### Post by groggyboy on 2006-12-03
> for the record, i like the look+programs of kde more than gnome
i'm with you 100% on that one!  ;) 

anyways, i'm not sure how to go about dealing with package keys using a gui in KDE - i wish i did.  i'd go with a gui instead of command line any day.

if you are willing to go into the command line, try this from a terminal (after you've added the repository in adept):```
wget http://beryl-mirror.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add - 
```
that command is specific to the repository mentioned in the link you posted, so it should work.  i actually took the command from the Ubuntu Wiki article on installing beryl.

a couple of links that may be of interest to you:[URL="https://help.ubuntu.com/community/Repositories/Ubuntu"]
the Ubuntu Wiki article on managing repositories[/URL] - unfortunately, it's a little GNOME-centric.  it's very indepth.
[the Ubuntu Wiki article on managing repos with adept]("https://help.ubuntu.com/community/Repositories/Kubuntu") - very brief, and all the important stuff has already been mentioned in this thread.
[the Ubuntu Wiki HowTo for installing beryl]("https://help.ubuntu.com/community/BerylOnEdgy") - if the HowTo you are using goes wrong! :p 

have fun!

---

