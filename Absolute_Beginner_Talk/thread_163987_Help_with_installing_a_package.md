---
title: "Help with installing a package"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-04-21
Hi, I am trying to install a package from a website and here are the install directions

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


I  "cd" to the folder the tar.gz is in...Then i type ./configure but all it says is "no such file or directory"

Please help

---

### Post by wdbreen on 2006-04-21
What package is it exactly that you are trying to install?

---

### Post by towsonu2003 on 2006-04-21
did ou extract the tar.gz first? right click file and select "extract here" or ```
cd /path/to/targz/ 
tar -xzvf nameoftargz

```
than cd into that directory (where the file is extracted) and go from there. But **before** doing this, check if this package is included in Synaptic.

---

### Post by catlett on 2006-04-21
There are a few obvious things wrong unless your not printing the entire directions. A tar.gz file is like a "zip" file in windows. You can't configure a tar like you can't install a zip file. You can untar by right clicking on it and choosing "extract here". ((Didn't see the previous post I was inside the reply panel, excuse the redundancy))
Also you can't just write /configure, you have to tell the computer what to configure. As well as what to make etc. All commands have to tell how to execute that command and what to execute it on(the program or file's name). 
Post the link to the program so maybe someone can recognise it and/or post the exact directions from the site.

---

### Post by zxcvbnm on 2006-04-21
.....@ubuntu:~/Desktop/untitled/libgcrypt-1.2.1$ tar -xzvf libgcrypt-1.2.1 
tar: libgcrypt-1.2.1: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


That is what i get

here's the link

[http://www.gnupg.org/](http://www.gnupg.org/)

---

### Post by towsonu2003 on 2006-04-21
[QUOTE=zxcvbnm].....@ubuntu:~/Desktop/untitled/libgcrypt-1.2.1$ tar -xzvf libgcrypt-1.2.1 
tar: libgcrypt-1.2.1: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


That is what i get

here's the link

[http://www.gnupg.org/](http://www.gnupg.org/)[/QUOTE]
use this instead, because it is in the repositories/synaptic/apt-get
```

#connect to internet
sudo apt-get update
sudo apt-get install libgcrypt11
```
its version is 1.1.12 though, which usually doesn't matter. 

few notes:
* it seems you already extracted the "zip" file, so ./configure in that directory was supposed to work. 
* see this about installing software in ubuntu: [http://www.pcmech.com/show/os/917/2/](http://www.pcmech.com/show/os/917/2/)
* before compiling anything in ubuntu, first check whether the repos have that package (see above link).

**edit**: gnupg is also already in the repositories (see above link). use synaptic to install or install with ```

#connect to internet
sudo apt-get update
sudo apt-get install gnupg

```

---

### Post by zxcvbnm on 2006-04-22
Damn  i am stupid i should of checked first...LOL

Thanks for the help

I am going to bookmark that site..LOL

---

### Post by guitaristz on 2006-04-22
Catlett,

I was just trying to figure this out, too. I've downloaded to the desktop
jack-audio-connection-kit-0.100.0.tar.gz
Now, how does one install it after "extract here" ?
I'm as green as green here so thanks very much.

---

### Post by Mustard on 2006-04-22
[QUOTE=guitaristz]Catlett,

I was just trying to figure this out, too. I've downloaded to the desktop
jack-audio-connection-kit-0.100.0.tar.gz
Now, how does one install it after "extract here" ?
I'm as green as green here so thanks very much.[/QUOTE]

Jack-audio-connection-kit is another one that is already in the repositories.

> mustard@slave:~$ apt-cache show jackd
Package: jackd
Priority: optional
Section: sound
Installed-Size: 316
Maintainer: Junichi Uekawa <dancer@debian.org>
Architecture: i386
Source: jack-audio-connection-kit
Version: 0.99.0-2ubuntu1
Depends: libc6 (>= 2.3.2.ds1-11), libc6 (>= 2.3.2.ds1-4), libjack0.80.0-0 (= 0.99.0-2ubuntu1), libreadline4 (>= 4.3-1), libsndfile1 (>= 1.0.2-1)
Suggests: qjackctl, jack-tools, meterbridge, libjackasyn0
Filename: pool/main/j/jack-audio-connection-kit/jackd_0.99.0-2ubuntu1_i386.deb
Size: 84818
MD5sum: 0fba5bdd87b4ebf6ab3b3736d5492014
Description: JACK Audio Connection Kit (server and example clients)
 Low-latency sound server. JACK allows the connection of multiple applications
 to an audio device, as well as allowing them to share audio between
 themselves.
 .
 See <http://jackit.sourceforge.net/> for more info.
 .
 This package contains the daemon jackd as well as some example clients.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


```
sudo apt-get install jackd
```

---

