---
title: "pymol not install"
date: 2005-05-19
forum: Apple PPC Users
---

### Post by open_flax on 2005-05-19
hello
i have ibook G4 and i prove to install pymol but it depends by python 2.3. on my sistem i have installed  python 2.3 and 2.4  so when i use synaptic to install pymol it not found python 2.3 and go out. 
have you any solution?
thanks

---

### Post by stef on 2005-05-28
hi,

hmm had the same problem .. best inform the package maintainer .. in the meanwhile try to download the packes pymol and python-pmw (google for ubuntu and the package [apt-get should be able to do this as well, i guess]) then install them with sudo dpkg -i --force-depends. then they are on your system. okay then remove the symlink /usr/bin/python which is directing at python2.4 and create one directing to 2.3 by sudo ln -s python2.3 python.
pymol runs on my powerbook this way .. but it's an ugly hack ...

regards stef

---

### Post by stef on 2005-05-28
still not nice... but a little better :-)

edit the /usr/bin/pymol script. change the python in the last line to python2.3.

--
stef

---

### Post by stef on 2005-05-29
$  sudo  apt-get build-dep pymol
        $  sudo apt-get -b source pymol
        $  sudo dpkg -i pymol_0.97-1ubuntu1_powerpc.deb

---

### Post by open_flax on 2005-05-31
hello
 i do to another way. i install every dependencies with synaptic and from sources install pymol. infact when i make the comand:
 $ sudo apt-get -b source pymol
i will turn back an error.
 :)

---

