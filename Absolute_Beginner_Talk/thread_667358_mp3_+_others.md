---
title: "mp3 + others"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by pedrom169 on 2008-01-14
just installed the win32codecs using this guide
[http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml]("http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml")

i tested by putting a cd in and it worked perfectly
but when i tried to play a mp3 it didnt work
and when i tried to play a .avi file it said i dont have divx4 and MPEG 1 codec. which on the list at the bttom of the page. said it had

how to get these codec's

i dont have internet on the ubuntu computer.

thanks

Peter

---

### Post by szymon_g on 2008-01-14
show me your /etc/apt/sources.list :>

//******************//
btw, why you didn't use this way to install mplayer ? 

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Multimedia_Players](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Multimedia_Players)

---

### Post by pedrom169 on 2008-01-14
sorry im new to this. how do i get that list?

//************************//

if thats easier. how do i get rid of the codecs i have at the moment to start that one.
and
can i do that without internet on that pc?

---

### Post by szymon_g on 2008-01-14
the easies way to get this file is 

cat /etc/apt/sources.list

(small hint: when you type cat /etc/apt/so<tab> - it will autocomplate the file. or, if there is more than one, will show you a list of files. really usefull, i couldn't live without it :>)

read about editing it (adding repositories). 
if you wanna change it, type

sudo gedit /etc/apt/sources.list

/// *********
unfortunatelly, ubuntu (and a lot of other distros) are almos useless without sort of internet connection :/

"how do i get rid of the codecs" - unfornutatelly, i didn't understood :< (mea culpa: english is not my native tongue)

---

### Post by pedrom169 on 2008-01-14
i mean delete the current codec's that is on my computer and start fresh and use that guide for mplayer

---

### Post by szymon_g on 2008-01-14
the easiest way 

sudo aptitude install mc

than

sudo mc

than navigate into this directory where you have these codecs, select it an F8 :>

////////*** 
of course you can use synaptic for it :> depands what you prefer

---

### Post by pedrom169 on 2008-01-14
typed in sudo mc.

and it said command not found

---

### Post by szymon_g on 2008-01-14
did you installed mc :?

from console :

sudo aptitude install mc

in synapcit you have to find this package

than sudo mc


////////////////
or try 

sudo rm -rd /path/to/codecs

---

### Post by pedrom169 on 2008-01-14
yes i did.
installed it but wont sudo mc.

---

### Post by szymon_g on 2008-01-14
:o

so prabably it's not in your PATH variable...
anyway : try 

sudo rm -rd /path/to/codecs/installed/by/you

---

### Post by pedrom169 on 2008-01-14
that worked. ill try and do the guide for mplayer. ill ask for help if need.

---

### Post by philinux on 2008-01-14
click the medibuntu link below and follow the procedure.

---

