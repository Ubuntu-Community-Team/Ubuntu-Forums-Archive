---
title: "Can I install .rpm or .tgz achives in ubuntu?"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by jazzinsa on 2006-02-07
Ok so I've took the dive from windows to linux (or is it maybe a step up?) 
Now installed, I obvousely need to start installing software that I need to use. I have found a program that could replace my old windows program and its in a .rpm file or a nother one in a .tgz file. 

NOW WHAT? I download it and then?

If somewone can help me please.

Jazz...

---

### Post by kaamos on 2006-02-07
This can be done with alien. It is not guaranteed to work, but (for me atleast) it often does the job
```
sudo apt-get install alien
sudo alien -i name_of_file.rpm
```
More info
```
man alien
```

---

### Post by Scotland on 2006-02-07
can't remember the exact syntax (in xp at the moment) but you can use the alien command for this.

Dougie.

---

### Post by Gcool on 2006-02-07
You can do it as follows (type the commands in console):

*For the rpm file: rpm -i filename.rpm
*For the tgz file: tar -xvzf filename.tgz
                        ./configure
                        make
                        sudo make install

---

### Post by jazzinsa on 2006-02-07
thanks i' will try all of the above,
what happend to double click on the setup.exe? :confused:

---

### Post by kaamos on 2006-02-07
Clicking "Apply" in synaptic replaced it. :) Got rid of the annoying wizards as well..

And for .deb files outside synaptic:

[img]http://people.ubuntu.com/~mvo/gdebi/gdebi-2.png[/img]

in ubuntu 6.04 once it released. Rpms are not really designed to be installed on debian (ubuntu) systems.

---

