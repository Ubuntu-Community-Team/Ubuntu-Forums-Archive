---
title: "The process of installation"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-02-11
Ok, I believe I've got this figured out. If I have found a program that isn't found on Synaptic, Adept, etc, and I download the tar. I would then decompress it, run terminal, cd to the directory of the program I wish to install. I know about the ./configure, make, and make install commands. But I am confused about the ./configure command. Is it used like "home/username/Desktop/nameofprogramiwanttoinstall/configure", or is it left as dot slash configure?

I'm sorry for being so ignorant and needy. Thanks

---

### Post by seshomaru samma on 2007-02-11
```
./configure 
```

for more info read [how to install anything in ubuntu]("http://www.cutlersoftware.com/ubuntuinstall/#installing_a_package_manually")

---

### Post by macruadhi on 2007-02-11
ok, tried the ./configure command, RTFMed and this is what I got

eric@eric-laptop:~$ cd /home/eric/Desktop/gnucash
eric@eric-laptop:~/Desktop/gnucash$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

what path would I find the compiler under? The path the program I want to install or another general path?

---

### Post by 3rdalbum on 2007-02-11
in that terminal, put in the command:

```
sudo apt-get install build-essential
```

Now, depending on what program you've downloaded, your configure step should work.

---

### Post by macruadhi on 2007-02-11
Thanks, that worked more. Now I need

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

---

### Post by adza on 2007-02-17
i was also getting this message, however in synaptic package manager, click on the perl programming language tab and then search for XML Perl, you will find a lot of packages that are available for parsing XML... although, if like me, you do this and try to configure something, you will probably get another error saying you don't have GLIB installed.. that's next... :) This is also my first time trying to install something using makefile etc... :S

---

### Post by az on 2007-02-17
since gnucash is laready in the repositories, you can use the source repository to get all the dependencies for building it.  Enable th deb-src repo for universe, updat eand run

sudo apt-get build-dep gnucash

and that should install everything you need to build the version that is in universe.  Maybe that will be enough to build the version you want.

---

### Post by adza on 2007-02-18
Also, i've now found that you can sudo apt-get build-dep [packagename] and this will build the dependancies for the package required. This of course, is true for the supported ubuntu repositories, as for the others.... as it was quoted to me, a definate 'maybe' ;)

---

