---
title: "Installing downloaded files."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Munkie2983 on 2007-03-19
I just switched from xp to linux, have been using it for 2 days now. Got the basics going on it and now I would like to expand and get some things up and running.I have no idea how to install downloaded files.I realize this is probably alot more simple then I seem to be making it. I have downloaded some drivers and other programs in .tar.gz/bz2 file format. I'm using Ubuntu 6.06 that i got with my "Official Ubuntu Book". How do you install those files? Ive been racking my brain and have read through the "add aplications" chapters of the book. Am I not seeing the forest through the trees? Ive used the add/remove prog synaptics packager and even tried using the shell program with "apt-get" and "dpkg". PLEASE HELP!

---

### Post by bruenig on 2007-03-19
Ok first make sure that the applications you are installing aren't available via apt-get. If they in fact aren't available via apt-get. You need to first get build-essential.
```
sudo apt-get install build-essential
```

Then you need to extract the tar.bz2
```
tar xf whatever.tar.bz2
```

Then you need to change into the new directory
```
cd whatever
```

Then look around to see if there is a README or INSTALL file and then read those, generally if everything is normal and it is source you will have to issue the following
```
./configure # make sure this doesn't give you an error
make
sudo make install
```

---

### Post by Munkie2983 on 2007-03-20
For some reason the "apt-get build-essential" doesnt work. It give me an invalid operation "build". Lastly the one file i got to configure but the make/make install gives me the same invalid argument only with "make" I'm starting to think Ubuntu is allergic to me.

---

### Post by zvacet on 2007-03-20
```
sudo aptitude install build-essential
```

---

### Post by Efwis on 2007-03-20
to get the make to work you will have to install the build-essential program.

use this command to get it

```

sudo aptitude install build-essential

```

when you did the apt-get you forgot to add **install**

---

### Post by Munkie2983 on 2007-03-21
Still not quite seeing the forest...I have build-essentials installed, ran ./configure, it makes Makefile.am and Makefile.in but when i try $sudo make install, it still isnt working. Below is what im getting in terminal. Do I need to input a file after install? 

```
munkie2983@Munkie2983:~/totem-2.18.0$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
munkie2983@Munkie2983:~/totem-2.18.0$
```

---

### Post by doctapeppa on 2007-03-21
If totem is what you are trying to install:

[HTML]sudo aptitude install totem-gstreamer-firefox-plugin[/HTML]

---

### Post by Munkie2983 on 2007-03-21
THanks but thats an older version then i already have. There have been several things that i get to the "make" point and they always give me the same error....I just happend to be doing totem at the time for the example.

---

### Post by cowlip on 2007-03-21
the order is this:

1. ./configure
2. make
3. sudo make install

Did you do all three steps, like make before make install?

---

### Post by Munkie2983 on 2007-03-21
Yes I have and or did. I still get that same error. Im starting to think i'm "special" as far as ubuntu.

---

### Post by bruenig on 2007-03-21
You need to make sure that the ./configure is going through smoothly. If it is putting out an error, then that means you are missing a dependency. Look at the error, it will tell you what the problem is, and try to find that dependency in the repository. Install the dependency and give it another shot. Keep going until you get all the way through configure without an error message, and then do make and sudo make install.

---

