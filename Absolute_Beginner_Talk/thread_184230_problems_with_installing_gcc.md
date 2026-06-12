---
title: "problems with installing gcc"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by aoiz on 2006-05-29
I'm a newb to Linux, without to much experience with the shell.
I need to install gcc for further installments, because everything requires it.

Eventually I downloaded the gcc package gcc-4.1.1 and I tried to install it.
I unzip it and move to the directory, in the shell, and I type:

./configure

and the problematic output is this:

checking for gcc ... no :-k 
checking for cc ... no
configure: error: no acceptable cc found in PATH$

What could be missing and how can I get it? Is PATH$ the PATH-environment Variable?

I really would appreciate some help here, because otherwise I can't proceed with anything at all!:-(

---

### Post by mscman on 2006-05-29
You shouldn't need to download any source packages.  All you have to do is either open Synaptic Package Manager and search for the package 'build-essential' or, if you prefer terminal, run the command ```
sudo apt-get install build-essential
```
That should get you (most) tools you'll need for building stuff from source.

---

### Post by Sutekh on 2006-05-29
You can't compile gcc without gcc!  Kind of an endless loop huh?    Just install the package suggested by mscman.

Once you hav *any* version of gcc, you can compile a newer one if you want, or anything else.  However, installing by apt-get or Synaptic really is the way to and you should be aware of the advantages over compiling from source.

These links have some more good info on installing software (with borrowed explanation from aysiu; cheers) and you should really check them out.

[http://psychocats.net/ubuntu/installingsoftware.php]("http://psychocats.net/ubuntu/installingsoftware.php")

 -  Quick overview--explained in text. It applies to Ubuntu, Xubuntu, and Kubuntu.

[http://www.monkeyblog.org/ubuntu/installing/]("http://www.monkeyblog.org/ubuntu/installing/")

 - Very detailed and long with screenshots and explanations. Focused on Ubuntu for now, and mentions some features that are available only in Dapper.

---

