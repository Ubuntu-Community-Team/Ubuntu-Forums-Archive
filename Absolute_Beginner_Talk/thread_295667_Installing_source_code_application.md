---
title: "Installing source code application"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by manishk on 2006-11-08
I downloaded fwcutter.tar.gz using Windows onto my laptop bcoz Ubuntu doesn't have Broadcom Wireless Drivers.

How do I install it?

I unzipped and unarchived it onto my Home Folder.
When I run the ./configure or make command I get an error
bash:command (or file, I dont recall correctly) not found.

Pls help.

I dont have net access though Ubuntu, so cant use Synaptic

---

### Post by underdog on 2006-11-08
what files are in the directory? can you c & p the results of
ls -laF

---

### Post by dannyboy79 on 2006-11-08
you most likely are going to have to download the build-essential .deb  package which allows to compile stuff from source, it doesn't come with ubuntu by default which i don't know why. it's gotta suck not having net. 

a side question, if I get a program from source and I install it, where is a good place to put? i am talking about xiso, it's a program that can extract an xbox iso and upload it to a certain folder on my xbox all at once. currently it is just in a folder within my home directory and when i want to run it, I just type out the full path and the command but I am guessing there is a good suggestion for where i should keep my custom type appplications within my ubuntu cimputer. any help here. i am not trying to hi-jack your thread as this I believe will help you as well so that you'll know where to keep your program you are building from source.

---

### Post by po0f on 2006-11-08
dannyboy79,

/usr/local is a good choice.

When you run ./configure, it usually defaults to setting the PREFIX to /usr/local, meaning any programs it installs go in /usr/local/bin, any libraries it installs go in /usr/local/lib, any man pages it installs go in /usr/local/man, etc.  To make sure, run ./cunfigure with --prefix=/usr/local.

[EDIT]

Added explanation.

---

### Post by dannyboy79 on 2006-11-08
> **po0f said:**
> dannyboy79,

/usr/local is a good choice.

When you run ./configure, it usually defaults to setting the PREFIX to /usr/local, meaning any programs it installs go in /usr/local/bin, any libraries it installs go in /usr/local/lib, any man pages it installs go in /usr/local/man, etc.  To make sure, run ./cunfigure with --prefix=/usr/local.

[EDIT]

Added explanation.

i just remembered, i believe it's just a python script, so I just had to extract the tar file and then simply run xiso.py I think, that's why it didn't get put in /usr/local/bin. so, if I have a folder, gxiso-1.5, that has all this stuff in it; AUTHORS  build  build.bat  ChangeLog  gxiso.ico  gxiso.nsi  LICENSE  MANIFEST.in  NEWS  PKG-INFO  po  README  setup.cfg  setup.py  src  TODO. some of these things are files and some are folders, what can i delete? what should i move to /usr/local/bin, what should I move to /usr/local/bin/lib and so on and so forth. I think that when I want to run it, I go to the build folder although I forgot now because there's a gxiso.py within the src folder as well as the /build/scripts-2.4. they are different in size though, 1 is 32869 and the other is 32865. I don't know, i want a clean box, not crap everywhere, what do you suggest? if you're gonna help me, just say yes, you are and then I'll start a new thread. 


Sorry for hi-jacking, that wasn't my original intent!

---

### Post by Henry Rayker on 2006-11-08
dannyboy

I use a program called gxiso that sounds incredibly similar to what you have. It had installation instructions...I believe the command was

python gxiso.py install

or similar. To run the program, I just run gxiso.py...I deleted that folder in my home directory...

---

### Post by dannyboy79 on 2006-11-08
> **Henry Rayker said:**
> dannyboy

I use a program called gxiso that sounds incredibly similar to what you have. It had installation instructions...I believe the command was

python gxiso.py install

or similar. To run the program, I just run gxiso.py...give it a shot?


yeah, that's the same thing, I did install it and it works fine, i haven't tried running it without first having to change direcotries to where it is though, which is one thing I am trying to fix as well as just make my linux box "clean". meaning i don't want to have this installed in /home/daniel//300gb-ext3/downloaded/linux-programs/gxiso-1.5/build/scripts-2.4 and then some other program installed in /home/daniel/300gb-ext3/downloaded-programs/blah blah. I think i know that I'll put gxiso.py in /usr/local/bin but what about all those other f9olders that were used when i ran the install python script? should i move them to /usr/lib/ or /usr/local/lib or where?

---

### Post by dwblas on 2006-11-08
You should keep everything that didn't come with the system in /usr/local.  That way you only have to look in one place to find it, or uninstall it.  As for installing the program,  I would guess that setup.py would do that for you, although you may have to make it executable, or run python setup.py if it is not executable.  Check the README file.  It usually explains things.

---

### Post by CatKiller on 2006-11-08
> **dannyboy79 said:**
> you most likely are going to have to download the build-essential .deb  package which allows to compile stuff from source, it doesn't come with ubuntu by default which i don't know why. 

Yes it does. It's just not installed by default.

---

### Post by manishk on 2006-11-08
> **CatKiller said:**
> Yes it does. It's just not installed by default.

You mean the *Build Essential* package comes with the Ubuntu CD??

How do I install it? And if I install it? How do I install the source code application??

> **underdog said:**
> what files are in the directory? can you c & p the results of
ls -laF

I'll c & p it by tomorrow. 

> **dannyboy79 said:**
> Sorry for hi-jacking, that wasn't my original intent!

Hey thats ok...!

---

### Post by CatKiller on 2006-11-08
> **manishk said:**
> You mean the *Build Essential* package comes with the Ubuntu CD??

Yes. At least, it came with mine :)

> How do I install it?

You should be able to so a ```
sudo aptitude install build-essential
``` although it's possible that you'd have to add the cd as a repository if it isn't already. I seem to recall mine was added automatically, as part of the installation. You can do all of that through Synaptic. You should be able to install build-essential in Synaptic, too, should you wish.

>  And if I install it? How do I install the source code application??


It depends. ```
./configure
make
sudo make install
``` is a common method, once you've unpacked the tarball. There should be a file called README, or instructions where you found the source, that will tell you the specifics for the application you've chosen.

---

