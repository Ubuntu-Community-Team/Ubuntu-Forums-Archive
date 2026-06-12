---
title: "[SOLVED] error while compiling transmission"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-03-19
Okay, so I am trying to install the transmission bittorrent client. I'm pretty sure the version in synaptic is an older one.

I compiled it but then found out that I installed it without the GTK interface (doh!)

I don't know if I am supposed to uninstall that before trying to compile the program again.

I enter

./configure --with-gtk
then
make

I get this error

```
make[2]: Leaving directory `/home/alan/Desktop/transmission-1.06/gtk'
make[1]: Leaving directory `/home/alan/Desktop/transmission-1.06/gtk'
Making all in po
make[1]: Entering directory `/home/alan/Desktop/transmission-1.06/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: -o: not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/alan/Desktop/transmission-1.06/po'
make: *** [all-recursive] Error 1
```

what am I doing wrong?

---

### Post by glennric on 2008-03-19
The version in the repositories is 1.05.  So it is not a very old version at all compared to the 1.06 version you are trying to compile.  

As to getting it to compile just make sure you have all of the dependencies.  One way to achieve this is with
```
sudo apt-get build-dep transmission
```
and since you want gtk perhaps
```
sudo apt-get build-dep transmission-gtk
```
You might try downloading the source for the ubuntu transmission package and seeing what they do.

---

### Post by elchico04 on 2008-03-19
well do you know how I could select individual files to download from a  torrent instead of all of them? I saw from the screen shots of the newest version that you could do that.

How could you tell what version was in the repositories? Synaptic tells me that the version is 0.72.dfsg-1

---

### Post by elchico04 on 2008-03-19
nevermind. I got it to work. I just did a 'make clean' and 'make uninstall' and then tried again with gtk and it worked.

---

### Post by zvacet on 2008-03-19
@ **elchico04**

In Transmission click on** details>files**>uncheck them all and after that select ones you want to download.With right click on files you want to download you can choose download priority.

---

### Post by elchico04 on 2008-03-19
yeah I see that now. I didn't have that option in the version from the repositories.
It is still annoying that it automatically selects all of the files for downloading.
when I used uTorrent with windows it would ask me everytime.

---

