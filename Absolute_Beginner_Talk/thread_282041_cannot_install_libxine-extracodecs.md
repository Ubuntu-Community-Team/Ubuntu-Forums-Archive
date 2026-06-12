---
title: "cannot install libxine-extracodecs"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by eskimokid on 2006-10-22
i did type > sudo apt-get install libxine-extracodecs
and also > sudo aptitude install libxine-extracodecs
but it's not working!

when i typed > sudo apt-get install libxine-extracodecs the error said that 


> 
package libxine-extracodecs is not available, but is referred to by another package.  

This may meant that the package is missing, has been obsoleted, or is only available from another package.

E: package libxine-extracodecs has no installation candidate



when i typed > sudo aptitude install libxine-extracodecs
the error is like below

> No candidate version found for libxine-extracodecs.

so what should i do to enable MP3s ?

---

### Post by jorn on 2006-10-22
You have enabled the repositories?
and done a:
> sudo apt-get update

---

### Post by eskimokid on 2006-10-22
i did updated by both > sudo aptitude update
and
> sudo apt-get update

by the way...
what is repositories?
and how to enable it ?

---

### Post by jorn on 2006-10-22
That is from where you get all applications. The url-addresses are store in:
/etc/apt/sources.list. To open it, type or paste:
> sudo gedit /etc/apt/sources.list
(gedit is your editor)
now delete all the # in front of the url-addresses.
That will enable them.
Remember to save.
Then:
> sudo apt-get update
You are also able to do this by using Synaptic. System>Administration>Synaptic.Setting>Repositories

---

### Post by eskimokid on 2006-10-22
:cry: I'm using Kubuntu...
cant reach System>Administration>Synaptic.Setting>Repositorie s

---

### Post by jorn on 2006-10-22
[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

---

### Post by eskimokid on 2006-10-22
wow, thanks, it's working....
but...i still unable to play mp3 in amarok, but anyway, thanks alot jorn.
I'll try to find solution for playing mp3

---

### Post by jorn on 2006-10-22
Maybe this will help you:
[http://www.ubuntuforums.org/showthread.php?t=182902&highlight=mp3](http://www.ubuntuforums.org/showthread.php?t=182902&highlight=mp3)

---

