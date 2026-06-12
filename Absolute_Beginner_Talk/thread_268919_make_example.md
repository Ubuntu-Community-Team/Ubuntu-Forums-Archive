---
title: "make example"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-09-30
Could somebody show me an example of how make should be used.
(very annoying):neutral:

---

### Post by Frak on 2006-09-30
Serious

---

### Post by andiii on 2006-09-30
./configure
make
sudo make install (or sudo checkinstall)

---

### Post by Frak on 2006-09-30
Could you show it in baby steps
(I'm having a n00bie day)

---

### Post by solarwind on 2006-09-30
-> Open a terminal (I like konsole, but anything will do)

Make is used for compiling packages from source. First, untar or gunzip the package and enter the directory. Then do this:


#-> At the prompt, type:

./configure

#-> This configures the source package for the actual compilation, done by make

#-> Then, press enter and type:

make

#-> Then, press enter, once again, and type: 

sudo make install

#-> A prompt should come and ask for your password, type it.


As far as I know, checkinstall is a routing for make, not a program, so make NEEDS to be used.

Any problems? I'm happy to help.

---

### Post by andiii on 2006-10-01
Checkinstall is a replacement for "make install". It creates a .deb package, so the installed software will be installed with your package manager.

So you have downloaded a .tgz, .tar.bz or something. Go to the directory were the file is. Extract it with tar xvf filename.tar.xy (press TAB for completion, it saves some typing work).

The go into the directory: cd filename
There you do:

./configure
make
sudo checkinstall

Sometimes there is no configure script, so you just do the last 2 commands. However, there should be a README or INSTALL or something.

---

