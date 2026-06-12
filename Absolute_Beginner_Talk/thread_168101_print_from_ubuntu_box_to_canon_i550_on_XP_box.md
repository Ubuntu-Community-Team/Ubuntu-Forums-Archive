---
title: "print from ubuntu box to canon i550 on XP box"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-04-29
I am not exactly sure of where to begin to set up to print from my ubuntu box... My printer (Canon i550) is on the XP box. My searches have confused me with a bunch of different programs people use, and no real help for one as new and ignorant as I.

I guess I am wondering if anyone has come up with a simpler way or a clearer how to...

Thanks for any suggestions...

---

### Post by halitech on 2006-04-29
guess the most important thing to ask is this, is the printer shared on the XP box?

[Windows XP]("http://ubuntuforums.org/showthread.php?t=32190&highlight=canon+i550")

[Canon iXXX series]("http://ubuntuforums.org/showthread.php?t=10540&highlight=canon+i550")

---

### Post by jason.b.c on 2006-04-29
[QUOTE=Papa-san]I am not exactly sure of where to begin to set up to print from my ubuntu box... My printer (Canon i550) is on the XP box. My searches have confused me with a bunch of different programs people use, and no real help for one as new and ignorant as I.

I guess I am wondering if anyone has come up with a simpler way or a clearer how to...

Thanks for any suggestions...[/QUOTE]



:D  It's good to see that you haven't given up **Papa San**..!!:D

---

### Post by Papa-san on 2006-04-29
[QUOTE=jason.b.c]:D  It's good to see that you haven't given up **Papa San**..!!:D[/QUOTE]
 Hehehe... No... I can be pretty belligerent! I fought for three weeks before I got the wireless working,  and nearly did give it up. Once I got through that, I began to truly see the potential of ubuntu. Now, I am hooked! (I am trying to get my wife to see the light, but she is afraid to commit to the li'l guy in the tux!
:D 

Oh, I'm going to set the XP box to share. - Didn't think of that! Then I'll try the links in post #2...

Thanks!

---

### Post by halitech on 2006-04-30
Papa-san, you sound like me *L* and my girlfriend doesn't want to give up windows either, all cause a few programs don't work in wine and I haven't got the money for win4lin or crossover office :(

Let us know how you make out

---

### Post by Papa-san on 2006-05-03
So far so good on following everything in the links, except for not being able to get the 'libtiff3g' file I need. I have it on desktop as a .deb, but don't know how to install from there... Synaptic isn't able to find it, and I added every repository in the list... There is an error, though when trying to update the synaptic list:
"Could not download all repository indexes" h
ttp://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz: Sub-process gzip returned an error code (1)

apt-get install returns:
'Couldn't find libtiff3g'

---

### Post by catlett on 2006-05-03
```
 cd Desktop
```
```
sudo dpkg -i libtiff3g.deb
```
That should install the deb. I'm assuming it is called libtiff3g.deb. Obviously write in the real file name if it isn't.

---

### Post by catlett on 2006-05-03
Also instead of ```
 sudo apt-get install "whatever"
```
Try ```
sudo aptitude install "whatever"
```
Aptitude tries to deal with dependencies like your libtiff3g issue. It either tries to find it and install it or it will remove something that is causing the dependency issue. It doesn't always work but is worth a try.

---

### Post by Papa-san on 2006-05-04
Thanks to all so far...
I now have the latest libtiff3g installed. My list of printers did get bigger, but the canon 550i is not in that list. Would it be under something else? There is nothing with '550' in the name...

Am I barking up the wrong tree?

---

### Post by catlett on 2006-05-04
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus22.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus22.html) Is this your printer? If so this "might " help.

---

### Post by Papa-san on 2006-05-07
Thanks catlett... I think... I just don't know what I'm supposed to do.

I try the 'deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian) ./'
and it says:
```
john@ubuntu:~$ deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian ./
bash: deb: command not found

```

---

