---
title: "simpsons movie dvd on xubuntu"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by oneouncebrick on 2008-03-20
hi, i have xubuntu movie player, and when i put in the simpsons movie dvd, i see a pop up sayin.. : .Totem could not play 'dvd:/'.There is no plugin to handle this movie what can i do to make this work..?

---

### Post by x1a4 on 2008-03-20
Hi,

First add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your repositories. 

Second, install the following packages: 
[b]libdvdcss2
libdvdnav4
lsdvd
libdvdread3
libavcodec1d
non-free-codecs
[/b]

The quickest way to install these is to copy and paste the following into your terminal:
```
 sudo apt-get install libdvdcss2 libdvdnav4 lsdvd libdvdread3 libavcodec1d non-free-codecs

```

---

### Post by Nikhil Gohil on 2008-03-20
[HTML]http://ubuntuguide.org/wiki/Ubuntu:Gutsy[/HTML]

---

### Post by acirilo on 2008-03-20
it's a new encryption... the only player that will play the newest ones is VLC player

[http://ubuntuforums.org/showthread.php?t=727671&page=2](http://ubuntuforums.org/showthread.php?t=727671&page=2)

after installing a patched libdvdnav

follow these instructions to the letter..
[URL="http://tobias.rautenkranz.ch/debian/"]
http://tobias.rautenkranz.ch/debian/[/URL]

---

### Post by oneouncebrick on 2008-03-20
hey i installed what you told me to and this is what my terminal said... Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
 what now??

---

### Post by x1a4 on 2008-03-20
> **acirilo said:**
> it's a new encryption... the only player that will play the newest ones is VLC player

Not so, libdvdcss can manage latest encryption just fine.

---

### Post by x1a4 on 2008-03-20
> **oneouncebrick said:**
> hey i installed what you told me to and this is what my terminal said... Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
 what now??

Did you update the software list after adding medibuntu?  I should have mentioned it, sorry. 
```
sudo apt-get update
```

---

### Post by acirilo on 2008-03-20
> **x1a4 said:**
> Not so, libdvdcss can manage latest encryption just fine.

[http://ubuntuforums.org/showthread.php?t=727671]("http://ubuntuforums.org/showthread.php?t=727671")

all i know is it wouldn't for me

---

### Post by oneouncebrick on 2008-03-20
okay.. i just downloaded all of those plug ins still i et the same problem. it still wont play the simpsons movie when i put the disk in and try to play it through mplayer

---

### Post by acirilo on 2008-03-20
> **oneouncebrick said:**
> okay.. i just downloaded all of those plug ins still i et the same problem.

i know i'm not an expert..but try the instructions on this page

[http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)

---

### Post by oneouncebrick on 2008-03-20
tht did not work either. =[ also, those instructions are too hard to follow for me... i know im stupid on xubuntu.. lol i copy and pasted the thins that guy said but it still did not work

---

### Post by acirilo on 2008-03-20
> **oneouncebrick said:**
> tht did not work either. =[ also, those instructions are too hard to follow for me... i know im stupid on xubuntu.. lol i copy and pasted the thins that guy said but it still did not work

does OTHER encrypted movies play.. also did u try to install another player

such as mplayer, gxine etc

---

### Post by oneouncebrick on 2008-03-20
ROFL! thanks.. movie player didnt work, m player did! now...how do i unn install the old movie player? i dont need it anymore

---

### Post by acirilo on 2008-03-20
> **oneouncebrick said:**
> ROFL! thanks.. movie player didnt work, m player did! now...how do i unn install the old movie player? i dont need it anymore

just open up the installer program, search for the old movie player, right click it, select remove, then click apply

or command line > sudo apt-get remove totem


or whatever the name of the software is

---

