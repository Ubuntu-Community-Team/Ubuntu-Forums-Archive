---
title: "I want to compile mplayer ( Is gcc there in the install CD )"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by shivam on 2006-10-12
I want to compile mplayer but it says that gcc was not found.
I want to know that is there the source or installation files on the Ubuntu install cd or will i have to install gcc form the net ?

---

### Post by Bigbluecat on 2006-10-12
Insatall via synaptic.

---

### Post by shirilover on 2006-10-12
The following thread will be useful to you then.

[http://www.ubuntuforums.org/showthread.php?t=187709]("http://www.ubuntuforums.org/showthread.php?t=187709")

---

### Post by taurus on 2006-10-12
Yes, gcc is on the CD.  Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

```

p.s.  Don't forget to insert the CD into the drive!!!

---

