---
title: "How do I install from a tar file?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Tails Prower on 2007-06-18
Hi.

I found a bin/cue>Mpeg converter named VCDgear, and located the install files for linux. The file I got was [COLOR="Red"]vcdgear176-040415_linux.tar.gz[/COLOR]

I extracted the file to a directory ([COLOR="Lime"]VCDgear[/COLOR]) which contains these files
[COLOR="Blue"]CDI[/COLOR]  Changelog  Credits  [COLOR="Blue"]lang[/COLOR]  [COLOR="Lime"]vcdgear[/COLOR]  vcdgear.cfg

I ran apt-get install and it seemed to work, but mentioned something about not finding a package, and I can't run ./config.
```
tails@Greenhill:~/VCDgear/vcdgear$ sudo apt-get install vcdgear
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vcdgear
tails@Greenhill:~/VCDgear/vcdgear$ ./configure
bash: ./configure: No such file or directory
```

clearly, apt-get install accomplished nothing
```
tails@Greenhill:~/VCDgear/vcdgear$ sudo apt-get install myballs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package myballs
```

How do I get vcdgear into the apt-get package list? Am I following the right procedure to install from a tar file? What is the right procedure to install from a tar file? I appreciate any help.

---

### Post by willl on 2007-06-18
i'm no genius at this stuff but i seem to remember something about "make" and "make install" after un-tarring.

---

### Post by sessine on 2007-06-18
looks to me like you have downloaded a pre-compiled binary and therefore don't need to do anything special.  the vcdgear file is the executable, just execute it from the command line or create a desktop/menu item for it.

---

### Post by DBStevens on 2007-06-18
The packaging system doesn't install the contents of  a tar archive.

Usually one would untar the archive and follow the instructions contained there in.

---

### Post by EagleRock on 2007-06-18
apt-get only installs from your .deb repository (which is most likely the online Ubuntu repository).  To install from a .tar file, you need to compile it yourself using ./configure, make, and make install.

I recommend going to Applications > Add/Remove and searching for vcdgear under All Open Source Repositories before going through the manual install.  I'd check myself to see if it's in the list, but I don't have an Ubuntu install to see right now.

---

### Post by maximouse on 2007-06-18
Yes, like sessine said, it seems like a binary. Try to first "chmod +x vcdgear" to make it executable, and then run "./vcdgear"

---

### Post by Tails Prower on 2007-06-18
it was a binary file, and 
```
chmod +x vcdgear
./vcdgear
```
worked fine.

Thanks, everybody.

---

