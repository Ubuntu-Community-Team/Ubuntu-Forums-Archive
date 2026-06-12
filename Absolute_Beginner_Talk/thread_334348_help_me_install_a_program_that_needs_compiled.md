---
title: "help me install a program that needs compiled?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-01-08
I was looking for a gui based sfv/md5 checker/creator and found a program called Parano.  It doesn't have the deb package installer, but I downloaded

[http://www.gnomefiles.org/app.php/Parano](http://www.gnomefiles.org/app.php/Parano)

and read the install, which I had to download a library to get it going.  Anyway I went through all the way to make install, but not sure what to do now?

I double clicked on any sfv file and it didn't work and I tried Parano in the command line and that didn't work either.

---

### Post by ajmorris on 2007-01-08
can you post a screenshot of the files please?

also can you write down what you have run? like make install etc.

---

### Post by david_kt on 2007-01-08
Please check in the /usr/local/bin folder for the new file just created. It should be the program to run. This is provided you use default setting during installation.

You could also repeat the installation (./configure, make), but do:

[INDENT][/INDENT]make check

before sudo make install.
And you should also read if there is any error during installation. When you issue the command (./configure, make, sudo make install), it does not guarantee it is install unless it said so (no error during installation).

Regards,
DK

---

### Post by bone2006 on 2007-01-08
thanks for the help, here's the screenshot and these are the instructions I followed:


he simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

after this I'm a littel bit lost, sorry for my ignorance.

---

### Post by bone2006 on 2007-01-08
Here's also a link of exactly what I downloaded

[http://download.berlios.de/parano/parano-0.3.0.tar.gz](http://download.berlios.de/parano/parano-0.3.0.tar.gz)

---

### Post by shanepardue on 2007-01-08
I'd recommend using a program called "checkinstall" that makes it much easier to remove the program if ever you decide to remove it.

After you install "checkinstall" from the repos, simply type "sudo ./configure" then "sudo checkinstall". The directions thereafter guide you through the whole thing.

Now you can remove the software through synaptic if you needed to.

---

### Post by david_kt on 2007-01-08
Do you run:

      make install

That would not install anything.

You should run:

      sudo make install

instead, and then key in you password.

Regards,
DK

---

### Post by bone2006 on 2007-01-08
thanks for the recommendation. I'll get checkinstall

I did:
1) ./configure
2) make
3) make check
4) make install

I checked the instructions and it says it's in the right place, but not sure how I'm supposed to access this software or if it's possible i did something wrong?

thank you both for your responses

---

### Post by david_kt on 2007-01-09
> **bone2006 said:**
> thanks for the recommendation. I'll get checkinstall

I did:
1) ./configure
2) make
3) make check
4) make install

I checked the instructions and it says it's in the right place, but not sure how I'm supposed to access this software or if it's possible i did something wrong?

thank you both for your responses

===========================================================

As I have informed in earlier post, the last script should be:

[INDENT]4) sudo make install[/INDENT]

If you do

[INDENT]4)make install[/INDENT]

it would not install anything because it would try to change your system file, but will surely fail.

Regards,
DK

---

### Post by bone2006 on 2007-01-09
sorry if I wasn't clear
every command I did sudo infront of it.  So looking at this list:

1) ./configure
2) make
3) make check
4) make install

just imagine sudo infront of each command

---

### Post by bone2006 on 2007-01-09
I found a newer release of the software and went through the steps and now when I type in parano in the command line the software comes up and it's working.  I followed the same steps, but seems this new version is working.

Anyway I have other questions.  one is that I used the installcheck and really liked it and I saw that it created a deb file, does that mean if I reformated my HD, could U just run this deb file and install the program?  Could I send it to another friend who's running deb or is it system specific?

---

### Post by david_kt on 2007-01-10
> **bone2006 said:**
> sorry if I wasn't clear
every command I did sudo infront of it.  So looking at this list:

1) ./configure
2) make
3) make check
4) make install

just imagine sudo infront of each command


I see, then it should be ok. But actually you only need to "sudo" the last script. First to third script (normally) did not require sudo.

Regards,
DK

---

