---
title: "Where is Jahshaka!"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-04-03
Hi all, 

I've been reading alot about a video editing program for linux based systems called [Jahshaka]("http://www.jahshaka.org/"), it appears to be a decent editing program and it's for linux (say no more! :) )

I've had untold issues attempting to download and compile a tar ball, and even after adding extra repositories as specified over on the jahshaka wesbite I am still unable to install.

Has anyone actually managed to install this software, if so....how??

:)  thanks in advance.

---

### Post by Jussi Kukkonen on 2007-04-03
Suggestion: add details about the actual problems and the steps you took to solve them. Also link to any howtos you followed.

---

### Post by TURNER on 2007-04-04
Hi....here are the steps taken so far.

I was attempting to install jahshaka by compiling a tar ball downloaded from [sourceforge.]("http://sourceforge.net/projects/jahshakafx")

The how to, was located in German [here]("http://knecht.homelinux.net/phpBB2/viewtopic.php?t=380&start=0&postdays=0&postorder=asc&highlight=")

Hope you can understand some of the instructions there (i knew that learning German would be useful someday :) )

I used the nautilus command in order to move the tar ball to /opt file and then untarred the files into /opt.
Having then attempted a ./configure , make; terminal complained about permissions (I did sudo!) and bailed install.

Further to this I installed some dependencies as instructed using
Code:

```
apt-get install qt3-dev-tools-embedded qt3-dev-tools-compat qt3-dev-tools libqt3-mt-dev freeglut3 freeglut3-dev
```

I also added an extra repository in order to download the jahshaka deb, but theres no sign of it in synaptic or by using apt-get

any help will be appreciated!

---

### Post by gabuzo on 2007-04-18
Hi

This repository seems to work for me : 

deb [http://repo.jahshaka.org/ubuntu/dapper/](http://repo.jahshaka.org/ubuntu/dapper/) binary-i386/

---

### Post by Marsolin on 2007-04-18
[Jahshaka]("http://linuxappfinder.com/package/jahshaka") is also in the [Debian Multimedia (Marillat)]("http://www.debian-multimedia.org/") repository.

---

### Post by TURNER on 2007-04-22
Hi

Ive now added:

deb [http://repo.jahshaka.org/ubuntu/dapper/](http://repo.jahshaka.org/ubuntu/dapper/) binary-i386/ and the Debian Multimedia (Marillat) repository, however upon opening synaptic and searching for Jahshaka I am unable to locate anything.....ive definitely added and enabled the repro's correctly.

Any further ideas?

---

### Post by cpauquez on 2007-04-22
An alternative:

[http://lives.sourceforge.net/index.php?do=home](http://lives.sourceforge.net/index.php?do=home)

Ubuntu packages:

[http://www.getdeb.net/app.php?name=lives](http://www.getdeb.net/app.php?name=lives)

---

### Post by TURNER on 2007-04-22
> An alternative:

[http://lives.sourceforge.net/index.php?do=home](http://lives.sourceforge.net/index.php?do=home)

Ubuntu packages:

[http://www.getdeb.net/app.php?name=lives](http://www.getdeb.net/app.php?name=lives)

Thanks for the tip, looks like a promising piece of software!

---

### Post by imon9 on 2007-04-22
actually, ever since i moved to linux/xubuntu.. i've been trying to find a decent video-editor...

i've tried Live, kino, pitivi, kdenlive, cinerella... only thing i havent tried is jahshaka coz i cant seems to install it...

btw, in all those i tried: 
live: confusing and ugly GUI...hard to use. not really functioning so well
kino: nice interface...doesnt support enough import format 
pitivit: nice interface...just too young...can only add media and save them..no editing
cinerella: another confusing GUI... 
jahshaka: can't even install it yet :(

let me know if u all have better suggestion. and also, lemme know if jahshaka works nicely or not

---

### Post by Marsolin on 2007-04-22
> **imon9 said:**
> actually, ever since i moved to linux/xubuntu.. i've been trying to find a decent video-editor...

i've tried Live, kino, pitivi, kdenlive, cinerella... only thing i havent tried is jahshaka coz i cant seems to install it...

btw, in all those i tried: 
live: confusing and ugly GUI...hard to use. not really functioning so well
kino: nice interface...doesnt support enough import format 
pitivit: nice interface...just too young...can only add media and save them..no editing
cinerella: another confusing GUI... 
jahshaka: can't even install it yet :(

let me know if u all have better suggestion. and also, lemme know if jahshaka works nicely or not

A basic editor that I've had a lot of success with is [Avidemux]("http://linuxappfinder.com/package/avidemux").

---

### Post by Cypher on 2007-04-22
> **imon9 said:**
> actually, ever since i moved to linux/xubuntu.. i've been trying to find a decent video-editor...

i've tried Live, kino, pitivi, kdenlive, cinerella... only thing i havent tried is jahshaka coz i cant seems to install it...

btw, in all those i tried: 
live: confusing and ugly GUI...hard to use. not really functioning so well
kino: nice interface...doesnt support enough import format 
pitivit: nice interface...just too young...can only add media and save them..no editing
cinerella: another confusing GUI... 
jahshaka: can't even install it yet :(

let me know if u all have better suggestion. and also, lemme know if jahshaka works nicely or not
And to add to that, Lives cannot handle large movie files. What good is a video-editing program that has arbitrary limits on the file sizes??

Cinelerra indeed has a very confusing GUI, but I've been told that once you get the hang of it, things are very easy..and I'm determined to figure it out. :)

Regards

---

