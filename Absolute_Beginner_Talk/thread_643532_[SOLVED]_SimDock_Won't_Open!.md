---
title: "[SOLVED] SimDock Won't Open!"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by alsamman on 2007-12-17
I just installed SimDock apparently and when i try to open in it via Applications>Accessories>SimDock, it doesnt open, it just has the loading cursor but then it goes away and nothing happens. This is the output I got when i said sudo make install
```

Making install in src
make[1]: Entering directory `/home/kenan/Desktop/trunk/src'
make[2]: Entering directory `/home/kenan/Desktop/trunk/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'simdock' '/usr/local/bin/simdock'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/kenan/Desktop/trunk/src'
make[1]: Leaving directory `/home/kenan/Desktop/trunk/src'
make[1]: Entering directory `/home/kenan/Desktop/trunk'
make[2]: Entering directory `/home/kenan/Desktop/trunk'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'simdock' '/usr/local/bin/simdock'
test -z "/usr/share/simdock" || mkdir -p -- "/usr/share/simdock"
 /usr/bin/install -c -m 644 'src/bg.png' '/usr/share/simdock/bg.png'
 /usr/bin/install -c -m 644 'src/bg2.png' '/usr/share/simdock/bg2.png'
 /usr/bin/install -c -m 644 'src/bg5.png' '/usr/share/simdock/bg5.png'
 /usr/bin/install -c -m 644 'src/mark.png' '/usr/share/simdock/mark.png'
 /usr/bin/install -c -m 644 'src/question.png' '/usr/share/simdock/question.png'
test -z "/usr/share/applications" || mkdir -p -- "/usr/share/applications"
 /usr/bin/install -c -m 644 'simdock.desktop' '/usr/share/applications/simdock.desktop'
test -z "/usr/share/pixmaps" || mkdir -p -- "/usr/share/pixmaps"
 /usr/bin/install -c -m 644 'simdock.png' '/usr/share/pixmaps/simdock.png'
make[2]: Leaving directory `/home/kenan/Desktop/trunk'
make[1]: Leaving directory `/home/kenan/Desktop/trunk'

```
it doesnt seem that there were any errors but how come it wont open?
When I find it in my home folder there is a picture of a lock beside the SimDock folder, what does that mean?

---

### Post by wharp on 2007-12-17
I believe that means you don't have permissions to that folder.  Were you following instructions on how to compile/install SimDock?  If so, did they mention anything about a chown command?

---

### Post by alsamman on 2007-12-18
no they didnt they just said that i have to type
./configure
make
sudo make install

and thats it, could u please help me in finishing installation?

---

### Post by wharp on 2007-12-18
Actually, there's a .deb on [this post]("http://ubuntuforums.org/showthread.php?t=536461") that I installed from. That's probably the easiest way to do it.

---

