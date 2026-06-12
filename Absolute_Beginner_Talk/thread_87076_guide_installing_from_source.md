---
title: "guide installing from source"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by tuco100 on 2005-11-07
Hi i am new to linux and would like to ask is there any good tutorials/guides on how to install from source.

---

### Post by ubuntumaneh on 2005-11-07
See if this is too much:

[http://www.tldp.org/HOWTO/Software-Building-HOWTO.html](http://www.tldp.org/HOWTO/Software-Building-HOWTO.html)

If it is, there is easier ones. Now, usually the installation from source (generally it is a .tar.gz file)goes like that (in a terminal):

tar xzvf name.of.file.tar.gz

Then you go to the directory where it has copied the opened files, and look where it is a "configure" file, then type:

./configure

Then:

make install

---

### Post by shof2k on 2005-11-07
What do you want to install.  Do you mean the kernel, a specific program, or ubuntu as a whole?

Generally a good source folder will contain a make script, so all you need to do is type "(sudo) make" and "(sudo) make install".

Hope that helps.

---

### Post by tuco100 on 2005-11-07
Hi There thanks for the help the program i am trying to install is XDVDShrink for Linux . The advice i have been given is to 'Download dvdshrink-2.6.1-3mdk.tar.gz
extract it
sudo ./install.sh

which seems simple enough but what about this bit 
./configure

Then:

make install 

Is this basically the same command? also when you say go to the directory where it has copied the opened files, and look where it is a "configure" file, then type: the said command is this in a terminal or in the the actual "configure file" ? thanks

---

### Post by ubuntumaneh on 2005-11-07
It is different. In your case there is a installation script that make things easier. So, in a terminal, extract the program using:

tar xzvf dvdshrink-2.6.1-3mdk.tar.gz

Type ls (or dir) to see a list of programs. Probabily there will be a directory with the name dvdshrink. Enter in it using:

cd dvdshrink

Then type:

sudo ./install.sh

I  think this will be enough. The other thing I described is another common way to do it. Any proble, let me know of it. Good luck.

---

