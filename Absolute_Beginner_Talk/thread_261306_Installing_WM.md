---
title: "Installing WM"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by IngSoc on 2006-09-20
Any one help me install Windowmaker? I dloaded the tar but thats about as far as I know how to go... I know basic commands just dont know how to use them. Thanks.

---

### Post by charles.g.moore on 2006-09-20
is it a tar.gz or .tar.bz2?

---

### Post by IngSoc on 2006-09-20
WindowMaker-0.92.0.tar.gz

---

### Post by charles.g.moore on 2006-09-20
I cant tell you how to configure it but if you want to know how to install it:

navigate to where the file is located through the terminal

type tar -xvzf your_filename

type ls

go into the newly made directory

type ./configure

then type

make

then type 

sudo make install

---

### Post by IngSoc on 2006-09-20
ok on top of that where would files install on to my disk? what dir?

---

### Post by charles.g.moore on 2006-09-20
> **IngSoc said:**
> ok on top of that where would files install on to my disk? what dir?
what do you mean? after you do the tar -xvzf the files needed should be inside of that newly made dir

---

### Post by IngSoc on 2006-09-20
...Sorry this is another subjesct, im saying I installed a file on my computer but im not sure where it installed it self.... /usr/lib?

---

### Post by charles.g.moore on 2006-09-20
Truthfully I dont know but you could try going to a command prompt and typing

locate your_filename that will tell you everywhere it is installed and usually you can tell exactly where by looking for the branch closest to the root filesystem

---

### Post by IngSoc on 2006-09-20
configure:error no acceptable C compiler found in $PATH

---

### Post by charles.g.moore on 2006-09-20
you have no ocmpiler so you have to grab one
try sudo apt-get install gcc

---

### Post by IngSoc on 2006-09-20
sudo: time stamp to far in the future sept: 29 11:30

---

### Post by kerry_s on 2006-09-20
It's in the repo's

sudo apt-get install wmaker

I'm using it now, i installed it 3 days ago. it's 0.92 so it's up to date.

---

### Post by IngSoc on 2006-09-20
Beatifull.... I want it more now. Well how do I get out of this  repo? oh thanks by the way for the help.

---

### Post by kerry_s on 2006-09-20
look through your menu for "synaptic" it's the gui front end for apt-get. Then just search or scroll down to wmaker and right click choose install then press apply. If you don't see it make sure all your repo's are on(settings>repositories).

---

### Post by IngSoc on 2006-09-20
I think I got it thanks bro that was the winner there...

---

### Post by IngSoc on 2006-09-20
Which serial device is the x-10 cm17a controller connected to?

---

