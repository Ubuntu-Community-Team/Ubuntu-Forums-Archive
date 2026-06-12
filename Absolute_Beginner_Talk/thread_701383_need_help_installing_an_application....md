---
title: "need help installing an application..."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by dragon1964m on 2008-02-19
I found a grub editor that I want to install in my system. This is the application that I want to install [COLOR="Red"][[COLOR="Red"]Here[/COLOR]]("http://www.kde-apps.org/content/show.php?content=75442")[/COLOR]

I downloaded the "[[COLOR="Red"]source download[/COLOR]]("http://www.kde-apps.org/content/download.php?content=75442&id=1&tan=51266487")". I extracted the file to my home directory. Now what do I do? Your help would be greatly appreciated!
The instructions provided on the site left this n00b's head spinning!

---

### Post by bigken on 2008-02-19
this is the easiest way move the folder to your desktop

open up a terminal/console 

cd Desktop
cd kgrubeditor
mkdir build
cd build
cmake
make
sudo make install

this is kde program are you running kubuntu ?

---

### Post by Shippou on 2008-02-19
extract first the code into a directory. See first the instructions here: [http://www.freebsddiary.org/untar.php](http://www.freebsddiary.org/untar.php)

Then switch to that directory using cd command.

Then type all the commands stated at the site.

That should get you done. :)

---

### Post by yabbies on 2008-02-19
you need the build-essential tools found in synaptic

or open a terminal and 

```
sudo apt-get install build-essential
```

extract the krgubeditor to your Desktop
can do this easily by right clicking and using extract here(or something like that)

in a terminal again you need to navigate to the newly extracted file
if you extracted on your Desktop then it will be something like this

```
cd Desktop/name_of_file( kgrubeditor?)
```

now you need to make sure you have all dependencies to be able to install the program to check this in a terminal 

```
./configure
```
this will spit out in the terminal what programs you need to install an addition.
write them down and install them either with synaptic or the command sudo apt-get install

after installing all dependencies if needed: in command line again

```
make
```
this will compile all dependencies together.

now time to install:
```
sudo make install
```

clean up your tmp files you can do a 
```
sudo apt-get clean
```

to uninstall:
```
sudo make uninstall
```

---

### Post by Artemis_Fowl on 2008-02-26
Please consider using the official (Gutsy) .deb package. Instructions on how to do this can be found in the same page.

---

