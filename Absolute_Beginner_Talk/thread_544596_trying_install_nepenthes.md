---
title: "trying install nepenthes"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by samjeba on 2007-09-06
i am trying to install nepenthes

using following command
apt-get install nepenthes


i am getting following error;

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nepenthes


i used sudo -i before

---

### Post by oilchangeguy on 2007-09-06
are you sure you're using the correct spelling? a google search of your spelling turned up only info about a plant.

---

### Post by samjeba on 2007-09-06
here is the link 

[http://nepenthes.mwcollect.org/download](http://nepenthes.mwcollect.org/download)

:) true the word is related to plant, but this also related to open source project honeypot project

---

### Post by diatribe on 2007-09-06
if it is not in the reposotories it will not install using apt-get install, you will need to download either the source or a .deb file

E:  [http://nepenthes.mwcollect.org/documentation:readme](http://nepenthes.mwcollect.org/documentation:readme) has install instructions

---

### Post by samjeba on 2007-09-06
i am getting following error while installing with .deb file

error:dependency is not satisfiable:libc6


i am also have .tar.gz file but i am getting 

tar -xvzf nepenthes-0.2.0.tar.gz
tar: nepenthes-0.2.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by diatribe on 2007-09-06
you need to install libc6, or maybe the development headers

---

### Post by samjeba on 2007-09-06
i tried apt-get and here is the result

apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded


so do i have libc6 before , then i get same error again 
error:dependency is not satisfiable:libc6

---

### Post by Jandark on 2008-02-27
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package nepenthes

I think you shoould edit your /etc/apt/sources.list !

---

