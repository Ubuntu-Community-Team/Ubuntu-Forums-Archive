---
title: "new mplayer from repository"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by erikringmar on 2006-01-16
Dear all,

I just tried to get mplayer via the synaptic installer, but was told:

mplayer-386:
 Depends: libdirectfb-0.9-20  but it is not installable

How to get around this problem?

cheers,

Erik

---

### Post by Sef on 2006-01-17
Did you enable Multiverse?

Here is post on how to do it:

> Well I'll try to add more detail, but I am not good at writing documentation, nor do I know apt, anyway this is what I did.

1) edit /etc/apt/sources.list and uncomment the lines for universe 
(remove the "#" in front of the lines)

2) add a line similar to universe see the example; [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse
(note I am in Canada, I sugest you get a miiror closer to you)

3) download any extra codecs; wget [http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2)

4) unpack the codecs; tar -xvjf all-20050412.tar.bz2

5) become root ; su - root

6) change directory to /tmp; cd /tmp

7) create the directory for the codecs; mkdir /usr/lib/win32

8) move the "codecs" to the new directory; mv all-20050412/* /usr/lib/win32

9) install mplayer; apt-get install mplayer-586

Link:  [http://ubuntuforums.org/archive/index.php/t-76559.html]("http://ubuntuforums.org/archive/index.php/t-76559.html")

---

### Post by Perfect Storm on 2006-01-17
For codecs I'll recommend PLF: [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

```

sudo gedit /etc/apt/sources.list

```

add: 

[b]## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install w32codecs
```

also uncomment universe and multiverse in the sourcelist will properly solve your problem with mplayer.

---

