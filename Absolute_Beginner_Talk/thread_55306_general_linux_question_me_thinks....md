---
title: "general linux question me thinks..."
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by gord on 2005-08-08
hi :)

ubuntu looks great so far, but being a complete dunce when it comes to linux i have some quibbles. [note: ahh its great to be english and use words like that -_-]

as far as i understand, when using linux with less generalised applcations you have to download the source and build it yourself, ie: there is no general .exe for linux.
the problem here is i would have no idea where to start, the last time i did any compiling was a long time ago (and possibly in a galaxy far far away) for my own c++ apps, whenever iv needed to do any coding recently its been in python. 

so can anyone shed any light on the subject for me? and if you have to do what i think you have to do, is there any method to make the whole thing as painless as possible? 

thanks :)

---

### Post by ozzie123 on 2005-08-08
Well for Ubuntu you have .deb files which generally suitable for Ubuntu (note: *generally*). For everything else you have tarballs. You don't need to compile things to install it, all you need to do is unzip it (or untar-it if you want to call it that way), put it in usr/bin or whichever you like (to the extent possible under its manual), and voila it works.

However, things might be a little bit tricky if you are trying to install it via a tarball extension (.tar.gz, .tar.bz2, etc) especially with dependencies. So my advice, stick to .deb or .rpm (for redhat, fedora core, centos, etc). You could also use Xandros that supports both .deb or .rpm (with some exceptions along the installation of course).

---

### Post by PeP on 2005-08-08
two possibilities:

you got a thing.sh:
```

(sudo) sh thing.sh

```

you got thing.tar.gz:
```

tar -xvzf thing.tar.gz
cd thing-xxx  (xxx is the version string)
./configure 
make
sudo make install

```

you got thing.tar.bz2:
```

tar -xvjf thing.tar.bz2
cd thing-xxx  (xxx is the version string)
./configure 
make
sudo make install

```

you should also take time to read the README file and check that it is really not available :
```

apt-cache search some-functionality-or-name

```

enjoy.

---

### Post by dcraven on 2005-08-08
First you'll need to install your compiler and build toolchain like this:
```
sudo apt-get install build-essential
```

Secondly, you need to compile and install the app of course... The following instructions assume the package is called 'mypackage' and it resides in a tarball called 'mypackage.tar.gz' in the current directory. It also assumes that the package uses the GNU autotools build scripting system, which is generally the case.

```
tar xvzf mypackage.tar.gz
cd mypackage/
./configure
make
sudo make install

```
Now, assuming you have resolved all of the program's dependancies (either by skill or by luck), and assuming all went well, the program is installed and can be probably run like this:
```
mypackage
```

As I'm sure you've noticed, these instructions assume many assumptions :). Sometimes it works as descriibed, but sometimes it will require a little more playing. Best to find distrobution specific packages if possible. But in general, not required.

I should mention that when you install programs as described above, synaptic (apt) will have no knowledge of the package being installed. I suggest keeping the source tree around just in case you want to remove it from your system. To do this, enter the source directory (same directory as the one you were in when you ran ./configure etc above) and type:
```
sudo make uninstall
```

Now the program is removed, and you can delete the source tree.

Cheers,
~djc

---

### Post by dcraven on 2005-08-08
[QUOTE=ozzie123]For everything else you have tarballs. You don't need to compile things to install it, all you need to do is unzip it (or untar-it if you want to call it that way), put it in usr/bin or whichever you like (to the extent possible under its manual), and voila it works.
[/QUOTE]

Hmm.. Be careful as this will not work with programs written in some languages. For example programs written in C/C++ must be compiled. I think you might be dealing with scripts mostly (Perl/Python/Bash etc) that are all stuck in a single file. In general, just copying source files to /usr/bin will not work.

Conventionally, programs that are not installed using your distrobution's package manager are installed in /usr/local/bin instead of /usr/bin so that you can keep them seperate from the others. you make a mess in /usr/local, but try to keep the rest clean for your package manager (apt).

Cheers,
~djc

---

### Post by gord on 2005-08-08
tis generally for emulators and things like that. not so much major applications like open office. 

for example as far as i can tell the [zsnes](http://www.zsnes.com/) distrabution is just a plain c++ source. which would obviously need complation, now im not saying that i want to know howto get zsnes working. just a general howto for these things :)

which btw you all seem to have done rather well (and so quickly O_O). thankys all of yous :) 

unless i really am as dumb as i look, in that case i'll prolly be back here tommrow whining some more... oh well ;)

---

### Post by TristanMike on 2005-08-08
ozzie123, PeP, and dcraven those were some of the best explinations on how to "install" other software not in the repositories. With alot of unanswered questions, that helped take my nervousness away when working with those types of files.

Gord, if your interested in the ZSNES, it comes in Ubuntu's repositories.  You get those here....[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Or installation instructions for the newer version can be found here....[http://www.ubuntuforums.org/showthread.php?t=38526](http://www.ubuntuforums.org/showthread.php?t=38526)

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=gord]
as far as i understand, when using linux with less generalised applcations you have to download the source and build it yourself, ie: there is no general .exe for linux.
[/QUOTE]

Because there is no single Linux OS. Every version of Linux is a diffrent OS.

Here is the best way to get programs:

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

If I had to compile programs in Linux I would have quit a year ago.

You need to do this first:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

